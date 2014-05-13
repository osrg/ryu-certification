---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
137e8d47-9d90-4d72-8e3c-3edcc11cc022
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 52455b18-7c4a-44a8-8a21-7266f278b288
controller          : [11594557-dd0d-4b2a-bb02-18495c78dad0]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [17b4870c-43da-44cd-ac75-50c258503879, 220e016f-df5e-42d0-99cb-fdbc51f6d0ab, 87049804-8b6d-422d-a0e6-8501d25604fa, ebb8ebd6-850f-4774-b523-b92860acb917]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 11594557-dd0d-4b2a-bb02-18495c78dad0
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=557, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 17b4870c-43da-44cd-ac75-50c258503879
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [325e0979-fe20-483b-a3a8-6278ace88f46]
name                : eth22

_uuid               : 87049804-8b6d-422d-a0e6-8501d25604fa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [73aa4bc5-0f76-4bd7-bd05-187a4e759b0e]
name                : br0

_uuid               : ebb8ebd6-850f-4774-b523-b92860acb917
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2f92b299-7d72-40c7-80a0-9aa14ef47aef]
name                : eth21

_uuid               : 220e016f-df5e-42d0-99cb-fdbc51f6d0ab
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2d73d27b-d787-4049-88dd-9a4091b575b0]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 325e0979-fe20-483b-a3a8-6278ace88f46
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=897163282, tx_dropped=0, tx_errors=0, tx_packets=602392}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 73aa4bc5-0f76-4bd7-bd05-187a4e759b0e
admin_state         : down
duplex              : full
ifindex             : 146
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

_uuid               : 2f92b299-7d72-40c7-80a0-9aa14ef47aef
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
statistics          : {collisions=0, rx_bytes=1972403366, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1326617, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2d73d27b-d787-4049-88dd-9a4091b575b0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1230660000, tx_dropped=0, tx_errors=0, tx_packets=820440}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 75264fe5f1ceb73a33bcc8e1adb3ad9aad57237d
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Sun May 11 23:38:44 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Mon May 12 21:12:10 2014 -0700

    lib/classifier: Fix array splicing.
    
    Array splicing was broken when multiple elements were being moved,
    resulting in the priority order being mixed.  This came up when the
    highest priority rule from a subtable was removed and the subtable
    needed to be moved down the priority list by more than one position.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
