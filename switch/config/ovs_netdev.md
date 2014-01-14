---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
276d2421-6cb7-4e8c-8432-7a7b4b020db5
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
_uuid               : 1655f52e-e735-4764-9a82-bdfa9fc9f4bb
controller          : [6607364b-a952-4c8e-b538-cf152f0d1c51]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [dadc5972-721b-495e-82e8-16e6fb68051b, ecb37d8d-cf63-4d61-bc74-67d8fbd61632, f3259a80-ecba-4236-b9fd-d252c554b553]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6607364b-a952-4c8e-b538-cf152f0d1c51
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=302, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f3259a80-ecba-4236-b9fd-d252c554b553
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c142dbcf-dd57-41e5-8376-ca2f37276edc]
name                : eth7

_uuid               : ecb37d8d-cf63-4d61-bc74-67d8fbd61632
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [53089010-f805-4997-9f4a-add0d3b78848]
name                : br0

_uuid               : dadc5972-721b-495e-82e8-16e6fb68051b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aa391390-ff13-44d4-91a1-891ff7b5dbc8]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 53089010-f805-4997-9f4a-add0d3b78848
admin_state         : up
duplex              : full
ifindex             : 63
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : aa391390-ff13-44d4-91a1-891ff7b5dbc8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=367596, tx_dropped=0, tx_errors=0, tx_packets=3960}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : c142dbcf-dd57-41e5-8376-ca2f37276edc
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
statistics          : {collisions=0, rx_bytes=1174770, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=11880, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
