---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
afb9305a-2830-4e08-824d-f03aa77cb85c
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
_uuid               : 3df884d1-c84c-49f9-bfd0-eb2188872cfc
controller          : [5176ad45-4c72-4e10-933b-ecae9b85cdd7]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [38632696-4b09-4b8c-8b26-57519a1522bf, 64073e99-a106-43a9-8865-8c3f9ab1032c, a78be89e-d2d4-4c19-aca3-2fc9bc1a1c12]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5176ad45-4c72-4e10-933b-ecae9b85cdd7
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=357, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 64073e99-a106-43a9-8865-8c3f9ab1032c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [abc7c625-e576-4c8f-abe4-71733e3d65a5]
name                : br0

_uuid               : a78be89e-d2d4-4c19-aca3-2fc9bc1a1c12
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3cf5c1cd-8747-4fa2-a4f9-d01497495018]
name                : eth7

_uuid               : 38632696-4b09-4b8c-8b26-57519a1522bf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [22092e06-3583-425b-988e-e9446fe62567]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : abc7c625-e576-4c8f-abe4-71733e3d65a5
admin_state         : up
ifindex             : 125
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

_uuid               : 3cf5c1cd-8747-4fa2-a4f9-d01497495018
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

_uuid               : 22092e06-3583-425b-988e-e9446fe62567
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit dfe37e6abd276de01f686bbdf28cbf48e92cd1dc
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Tue Jan 21 14:23:27 2014 -0800
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Tue Jan 21 14:24:06 2014 -0800

    bfd: Add bfd_src_ip and bfd_dst_ip.
    
    This commit adds two new options, bfd_src_ip and bfd_dst_ip
    respectively, which allows user to configure the source and
    destination IP address of bfd control packet.  If the user
    specified address cannot be parsed, the default address
    will be used.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
