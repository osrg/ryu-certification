---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
adf9669e-03c6-48c8-81ff-e8d472db27f1
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a943a3c0-7a7b-4843-970e-a2cda46782b8
controller          : [b12b811b-8785-4efc-846f-11e6179dbb67]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [572929e5-f1e6-454e-bbfd-0831a0fa211f, 58b92255-4def-41e1-af27-12767061d4fc, 6a83e1df-8b2c-45ff-a9e6-b7d0b24c3f92, cdff2ba2-3486-41ee-b9cd-658586f75dfa]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b12b811b-8785-4efc-846f-11e6179dbb67
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=1006, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 58b92255-4def-41e1-af27-12767061d4fc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2a896e93-8541-4cb6-8d44-6fde894241cc]
name                : eth21

_uuid               : 572929e5-f1e6-454e-bbfd-0831a0fa211f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e48d3719-c3b1-48a2-9501-a14fd67b3c15]
name                : br0

_uuid               : cdff2ba2-3486-41ee-b9cd-658586f75dfa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [07589c7e-c729-4cb4-a173-e3102742960f]
name                : eth22

_uuid               : 6a83e1df-8b2c-45ff-a9e6-b7d0b24c3f92
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f1e4b961-af42-4f12-a459-7847a0c1c785]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f1e4b961-af42-4f12-a459-7847a0c1c785
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3201773204, tx_dropped=0, tx_errors=0, tx_packets=4997827}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e48d3719-c3b1-48a2-9501-a14fd67b3c15
admin_state         : down
duplex              : full
ifindex             : 328
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

_uuid               : 07589c7e-c729-4cb4-a173-e3102742960f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2475490534, tx_dropped=0, tx_errors=0, tx_packets=4529363}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2a896e93-8541-4cb6-8d44-6fde894241cc
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
statistics          : {collisions=0, rx_bytes=2697810756, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=10432773, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0ca30f6f9bef59e65e62e6273dc4d1d5849bcf4c
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Mon Jun 2 21:36:28 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Jun 2 10:25:29 2014 -0700

    ofp-errors: Duplicate instruction error
    
    Add OFPERR_OFPBIC_DUP_INST &#40;type = OFPET_BAD_INSTRUCTION, code = 9&#41;
    and use it for OpenFlow1.4+.
    
    For OpenFlow1.1 - 1.3 map this error to ONFBIC_DUP_INSTRUCTION
    &#40;experimenter = ONF, type = 2600&#41; which is proposed in
    OpenFlow enhancement proposal EXT-260 &quot;Add error
    code for duplicate instruction.&quot;.
    
    Previously ONFBIC_DUP_INSTRUCTION was used for OpenFlow1.3+.
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
