---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c307edb8-f6b7-432d-b6aa-49fa537728fc
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f132c2f0-c90a-4e81-aaae-753b67913b2c
controller          : [d1caca14-1420-4792-9cef-6ed61d43817c]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [007fa92e-97c8-45a9-900b-3415e6600c63, 95b753f5-4da6-4e06-a72d-0eeef903b69f, c7b6958a-2b86-449d-8a89-62156aa2e275]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d1caca14-1420-4792-9cef-6ed61d43817c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 95b753f5-4da6-4e06-a72d-0eeef903b69f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3f32a20d-08cc-4030-9262-eb7055137539]
name                : br0

_uuid               : 007fa92e-97c8-45a9-900b-3415e6600c63
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [37642bb5-abe9-4b37-bb93-f7af292a8638]
name                : eth8

_uuid               : c7b6958a-2b86-449d-8a89-62156aa2e275
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6c4f532e-766c-41f5-b3e4-195742504d46]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 37642bb5-abe9-4b37-bb93-f7af292a8638
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 3f32a20d-08cc-4030-9262-eb7055137539
admin_state         : up
ifindex             : 61
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 6c4f532e-766c-41f5-b3e4-195742504d46
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0934ebbad0fda79dfae38e2de62cca7f9c7227b4
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Jan 10 15:17:43 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Jan 13 15:45:31 2014 -0800

    ofproto-dpif: Un-wildcard nw_frag only for protocols that have fragments.
    
    The revalidator code in ofproto-dpif-upcall.c, in revalidate_ukey(),
    deletes any datapath flow for which the kernel reports wildcarded bits
    that userspace requires to be matched.  Until now, a couple of pieces of
    code in ofproto-dpif always marked nw_frag (which tracks whether a packet
    is an IPv4 or IPV6 fragment) as exact-match.  For non-IP protocols, this
    wasn't meaningful, so adding such a flow to the datapath and then receiving
    it back caused nw_frag to become wildcarded, so revalidate_ukey() always
    deleted them.
    
    This fixes the problem by only un-wildcarding nw_frag for protocols where
    it is defined (IPv4 and IPv6).
    
    Noticed while observing CFM traffic (which isn't IP based) over a tunnel.
    
    Reported-by: Guolin Yang &lt;gyang@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
