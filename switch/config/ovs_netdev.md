---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
aa3599c5-0694-4c4a-92b6-92367d72be26
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 81f92379-ae17-4328-81d7-0badd6bc88a2
controller          : [7a16ba20-f834-425f-9f12-b0a4c48123d2]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1b7bbc15-7736-4fbc-b267-8679a4a58273, 3f4006b3-6af1-4b21-95e8-3124dc03fcb3, 463f3a11-006e-43d8-91bb-9220738d53e1, 52e036b6-885b-44aa-b630-cc6bafc59e60]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7a16ba20-f834-425f-9f12-b0a4c48123d2
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=562, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1b7bbc15-7736-4fbc-b267-8679a4a58273
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fd2eea3f-dd2c-48c3-b8a7-29582ef9141e]
name                : eth22

_uuid               : 463f3a11-006e-43d8-91bb-9220738d53e1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9b2eea11-9b82-4c41-bd38-4f129c1df0b1]
name                : eth23

_uuid               : 52e036b6-885b-44aa-b630-cc6bafc59e60
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0cac7d75-fbc7-4082-a1a8-dc268b637f61]
name                : br0

_uuid               : 3f4006b3-6af1-4b21-95e8-3124dc03fcb3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [84bc603b-3fa3-422c-b722-958b8ba92bb4]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9b2eea11-9b82-4c41-bd38-4f129c1df0b1
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1500
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1498341000, tx_dropped=0, tx_errors=0, tx_packets=998894}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0cac7d75-fbc7-4082-a1a8-dc268b637f61
admin_state         : down
duplex              : full
ifindex             : 1139
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

_uuid               : fd2eea3f-dd2c-48c3-b8a7-29582ef9141e
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1500
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1752991782, tx_dropped=0, tx_errors=0, tx_packets=1175385}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 84bc603b-3fa3-422c-b722-958b8ba92bb4
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=2932323556, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1971510, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e58f91a15a38ad2d26d77b77b2f1c84f6c6b06dc
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Tue Apr 22 13:34:36 2014 +0900
Commit:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
CommitDate: Thu Apr 24 14:48:54 2014 +0900

    hmap_random_node: Improve distribution
    
    Improve random distribution for an hmap with a small number of nodes
    with the expense of the increased cpu cost.
    It would be a fair trade-off because the situation is rather common
    for bond, which is currently the only consumer of this API in tree.
    
    Consider 2 items, 4 buckets, no collision.
    
        bucket 0   item 0
        bucket 1
        bucket 2
        bucket 3   item 1
    
    The old algorithm picks item 0 if rand % 4 == 0.  &#40;25%&#41;
    Otherwise it picks item 1.  &#40;75%&#41;
    
    This change makes them 50%.
    
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
</pre>
