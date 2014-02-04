---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d4213a50-1b18-473b-8876-5620b1a54421
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
_uuid               : 8a3fc878-acbe-4987-b528-c740f1f983e9
controller          : [722787d0-1803-4c0f-a1b3-f3be7a2cafe1]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [8e806115-952b-4601-8b2f-81dc9f7ca560, 8f49563d-ec19-477a-b4ba-1a4a42a53fc1, aab9e2a1-0174-440a-b1ba-88a495615d78]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 722787d0-1803-4c0f-a1b3-f3be7a2cafe1
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=346, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : aab9e2a1-0174-440a-b1ba-88a495615d78
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1fdf1bb0-9c80-4ce0-8a77-91446956a13a]
name                : eth7

_uuid               : 8e806115-952b-4601-8b2f-81dc9f7ca560
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [30ca5d2a-043c-4b1c-b8a7-7aea51443c9a]
name                : eth8

_uuid               : 8f49563d-ec19-477a-b4ba-1a4a42a53fc1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fc705d2d-a591-46da-8e39-0e107470604e]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1fdf1bb0-9c80-4ce0-8a77-91446956a13a
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

_uuid               : fc705d2d-a591-46da-8e39-0e107470604e
admin_state         : up
ifindex             : 137
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

_uuid               : 30ca5d2a-043c-4b1c-b8a7-7aea51443c9a
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
commit 0a0857df473cad7e8ce610f10813c94569953f98
Author:     Joe Perches &lt;joe@perches.com&gt;
AuthorDate: Mon Feb 3 17:27:41 2014 -0800
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Mon Feb 3 17:27:41 2014 -0800

    datapath: flow_netlink: Use pr_fmt to OVS_NLERR
    
    Add openvswitch:  prefix to OVS_NLERR output
    to match the other OVS_NLERR output of datapath.c
    
    Signed-off-by: Joe Perches &lt;joe@perches.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
