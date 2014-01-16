---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f21f211b-0c61-40fa-88b7-eb4013294ecf
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d7b88dd8-2475-47c2-b50e-dbc89e0c2f5f
controller          : [df99e848-2139-4038-9b3a-d3f474d75684]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [44c0ccbd-2572-4352-82a0-2bbab9142764, b9fbbc4b-b5c3-438e-96b4-782dbb6a494f, e48369c6-787d-4326-bad6-3627eafdc85b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : df99e848-2139-4038-9b3a-d3f474d75684
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=346, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 44c0ccbd-2572-4352-82a0-2bbab9142764
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b82955a2-f361-4fa1-8202-608a100709d6]
name                : br0

_uuid               : e48369c6-787d-4326-bad6-3627eafdc85b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2dcee926-25de-414d-adf8-0df8e62dcbf7]
name                : eth8

_uuid               : b9fbbc4b-b5c3-438e-96b4-782dbb6a494f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a5e44d89-dfbe-458b-ac1b-3c2d8013205e]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a5e44d89-dfbe-458b-ac1b-3c2d8013205e
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

_uuid               : b82955a2-f361-4fa1-8202-608a100709d6
admin_state         : up
ifindex             : 97
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

_uuid               : 2dcee926-25de-414d-adf8-0df8e62dcbf7
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
commit b73c85181df9cc38231a42d6f8095dcb604d230a
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Wed Jan 15 17:17:02 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jan 16 15:09:14 2014 -0800

    netdev-linux: Read packet auxdata to obtain vlan_tid
    
    If VLAN acceleration is used when the kernel receives a packet
    then the outer-most VLAN tag will not be present in the packet
    when it is received by netdev-linux. Rather, it will be present
    in auxdata.
    
    This patch uses recvmsg() instead of recv() to read auxdata for
    each packet and if the vlan_tid is set then it is added to the packet.
    
    Adding the vlan_tid makes use of headroom available
    in the buffer parameter of rx_recv.
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Co-authored-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
