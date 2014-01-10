---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b24c8b03-8568-458e-8d8f-68d6aa586c78
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 826414a2-3f32-4b7c-8fd6-319765a77632
controller          : [4829fb96-99eb-44c0-8ead-7f74d42eee99]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1a80b65a-3dac-4686-8110-718bbe9d4ab3, 55fb37d6-b116-4a6d-ba63-088cec060718, e4eb6f99-c03f-4a42-b11b-8836d7e423d3]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4829fb96-99eb-44c0-8ead-7f74d42eee99
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=296, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e4eb6f99-c03f-4a42-b11b-8836d7e423d3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5162281b-08ae-403d-a907-c1c382e76a54]
name                : eth7

_uuid               : 1a80b65a-3dac-4686-8110-718bbe9d4ab3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6f8204f8-ca24-4194-b253-4569f9345664]
name                : br0

_uuid               : 55fb37d6-b116-4a6d-ba63-088cec060718
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [146411ef-1fb0-4f80-bf1b-8c1a766686af]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6f8204f8-ca24-4194-b253-4569f9345664
admin_state         : up
duplex              : full
ifindex             : 45
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

_uuid               : 5162281b-08ae-403d-a907-c1c382e76a54
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
statistics          : {collisions=0, rx_bytes=587385, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=5940, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 146411ef-1fb0-4f80-bf1b-8c1a766686af
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=183912, tx_dropped=0, tx_errors=0, tx_packets=1980}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit feb8a80bb9621f17ed0a249c79b0d02e9543e64a
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Jan 10 11:36:35 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Jan 10 11:36:35 2014 -0800

    ofproto: Add more thread safety annotations.
    
    These would have found the problem fixed in commit c7be3f559349 (connmgr:
    Fix attempt to take mutex recursively when exiting fail-open.).
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
