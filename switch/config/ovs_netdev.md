---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
12a3a197-4d9a-49b1-bcc8-338cd0b0acbd
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 26de2b5e-d876-4c34-a413-1ce72e650b28
controller          : [8856abad-d92b-4b88-a826-7a0aff6aa880]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [05fa9fc2-e784-4d9f-b6d0-11a6d4916923, 0da5e036-9599-4460-a25e-df943effa72c, 2ac2b271-d9c8-424a-8d6f-f5399d328447, 2e0d409a-49ec-4993-b488-e81ba492d99b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8856abad-d92b-4b88-a826-7a0aff6aa880
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=967, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2ac2b271-d9c8-424a-8d6f-f5399d328447
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [84504e77-2810-4834-ae27-b7ce67c30aa5]
name                : eth21

_uuid               : 05fa9fc2-e784-4d9f-b6d0-11a6d4916923
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c4fc1375-9650-427f-baa3-8e5e94252df1]
name                : eth22

_uuid               : 0da5e036-9599-4460-a25e-df943effa72c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [69a501bc-f8a3-4e76-a68c-27f262aa11ff]
name                : eth23

_uuid               : 2e0d409a-49ec-4993-b488-e81ba492d99b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e8413df2-58be-48b6-b801-447628d4ddb3]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 69a501bc-f8a3-4e76-a68c-27f262aa11ff
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1876507408, tx_dropped=0, tx_errors=0, tx_packets=6977628}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c4fc1375-9650-427f-baa3-8e5e94252df1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1423042426, tx_dropped=0, tx_errors=0, tx_packets=12426448}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e8413df2-58be-48b6-b801-447628d4ddb3
admin_state         : down
duplex              : full
ifindex             : 443
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

_uuid               : 84504e77-2810-4834-ae27-b7ce67c30aa5
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
statistics          : {collisions=0, rx_bytes=896129756, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26434545, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a532e683cf9b97e55d1959f6aeb562bfd9429127
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Wed Jun 11 11:07:43 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Wed Jun 11 11:09:51 2014 -0700

    lib/cmap: Simplify iteration with C99 loop declaration.
    
    This further eases porting existing hmap code to use cmap instead.
    
    The iterator variants taking an explicit cursor are retained &#40;renamed&#41;
    as they are needed when iteration is to be continued from the last
    iterated node.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
