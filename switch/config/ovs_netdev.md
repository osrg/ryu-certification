---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e694dc58-1a0f-4915-bf91-f4dc2c8ccd47
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b71d705d-96f3-411d-b335-1492eda424ad
controller          : [22c71e49-2aea-480a-8089-5cd573dbdff8]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [155323fc-d66a-4c90-a8d8-9da693573303, 6d6c3e12-c554-43a4-b66b-e4cbc037dd58, a07c8350-22f8-4668-9979-ee66a27397ea, c75c929f-651f-45e7-8fcd-d54a184013c6]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 22c71e49-2aea-480a-8089-5cd573dbdff8
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=967, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 155323fc-d66a-4c90-a8d8-9da693573303
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [63583e88-1124-411f-9262-5cc6c3b545f5]
name                : eth21

_uuid               : a07c8350-22f8-4668-9979-ee66a27397ea
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aef595bc-49f0-4bf7-9fa0-b5479c18de15]
name                : br0

_uuid               : 6d6c3e12-c554-43a4-b66b-e4cbc037dd58
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9bce06c7-f78b-4297-b95f-af3d32975d56]
name                : eth23

_uuid               : c75c929f-651f-45e7-8fcd-d54a184013c6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e4440d98-168e-4b6f-8f0c-046468ff50b7]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e4440d98-168e-4b6f-8f0c-046468ff50b7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1000606450, tx_dropped=0, tx_errors=0, tx_packets=12142534}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : aef595bc-49f0-4bf7-9fa0-b5479c18de15
admin_state         : down
duplex              : full
ifindex             : 402
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

_uuid               : 63583e88-1124-411f-9262-5cc6c3b545f5
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
statistics          : {collisions=0, rx_bytes=4022386780, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=25649363, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9bce06c7-f78b-4297-b95f-af3d32975d56
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=920065408, tx_dropped=0, tx_errors=0, tx_packets=6340000}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 80771642ad7d3627eb691775e7ed6f7d0b29e237
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Jun 5 15:27:31 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Jun 6 13:54:47 2014 -0700

    ofp-actions: Store cookie in network byte order in struct ofpact_learn.
    
    Most other code in Open vSwitch that works with flow cookies keeps them
    in network byte order.  Using network byte order in struct ofpact_learn,
    also, reduces the number of byte order conversions needed across the
    source tree.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Thomas Graf &lt;tgraf@suug.ch&gt;
</pre>
