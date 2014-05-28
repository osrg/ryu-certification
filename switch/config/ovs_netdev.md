---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f44c59c2-dde2-4249-b2d2-cd9b6b6ced38
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0a71f4b2-ba49-4884-8009-2d62a180b305
controller          : [7eda74aa-46a4-4b4c-a2c0-a2708a932aa8]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [45d4f7c5-0bf4-46e3-b473-a2499615ab3e, 6b622e43-73ef-4492-975b-2725e39f6fcd, 8499c9fd-770a-4575-8e65-71becbad0076, 941704bb-d884-4073-87a7-e883c7cf131b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7eda74aa-46a4-4b4c-a2c0-a2708a932aa8
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=1002, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 45d4f7c5-0bf4-46e3-b473-a2499615ab3e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ba99eaa2-cafa-49ce-af71-7c6c6674ce9f]
name                : eth23

_uuid               : 8499c9fd-770a-4575-8e65-71becbad0076
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [27b8500f-2ad6-4960-8600-4be001b6879d]
name                : eth21

_uuid               : 941704bb-d884-4073-87a7-e883c7cf131b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b3e5d886-ef38-4eeb-b1dc-358ee3d76d10]
name                : br0

_uuid               : 6b622e43-73ef-4492-975b-2725e39f6fcd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d82556a7-b384-40d7-a7f8-3712b6b324ac]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b3e5d886-ef38-4eeb-b1dc-358ee3d76d10
admin_state         : down
duplex              : full
ifindex             : 258
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : ba99eaa2-cafa-49ce-af71-7c6c6674ce9f
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1371881204, tx_dropped=0, tx_errors=0, tx_packets=3777899}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 27b8500f-2ad6-4960-8600-4be001b6879d
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=3473392651, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=5211667, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d82556a7-b384-40d7-a7f8-3712b6b324ac
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3136719198, tx_dropped=0, tx_errors=0, tx_packets=2103433}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 22ba480908ee529bf0853ede2b971d3c5da23c94
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Tue May 20 16:42:37 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed May 28 09:54:32 2014 -0700

    ofproto-dpif: Remove unused flows.txt from fin_timeout test
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
