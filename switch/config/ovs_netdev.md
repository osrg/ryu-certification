---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3a589c86-dc3c-4451-a9a1-6a67ea789eb8
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
_uuid               : 56888f18-b68a-42bc-a228-38246a4f449c
controller          : [d6a5458a-6aa3-4161-be0c-c12f45bc8215]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [26e6b289-d32a-44f4-89f4-3440c687af9a, 393e3d16-c148-4eb8-96a3-14ac96c58761, 89286ea1-1cda-4966-9def-1832b97f4851]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d6a5458a-6aa3-4161-be0c-c12f45bc8215
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=382, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 89286ea1-1cda-4966-9def-1832b97f4851
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1af9b8d8-097d-4f33-9190-e6e4eb49632f]
name                : eth7

_uuid               : 26e6b289-d32a-44f4-89f4-3440c687af9a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2e2d4460-41a5-47fc-95a3-d843ba580214]
name                : br0

_uuid               : 393e3d16-c148-4eb8-96a3-14ac96c58761
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9ea294f8-67ba-48d1-9286-5819995de42c]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9ea294f8-67ba-48d1-9286-5819995de42c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4952472, tx_dropped=0, tx_errors=0, tx_packets=52807}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 1af9b8d8-097d-4f33-9190-e6e4eb49632f
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
statistics          : {collisions=0, rx_bytes=3067486810, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72678104, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 2e2d4460-41a5-47fc-95a3-d843ba580214
admin_state         : up
duplex              : full
ifindex             : 668
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 32260212a0687b6d14544a93a17363683bf41ea5
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Thu Mar 13 15:52:55 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Mar 20 15:01:45 2014 -0700

    ofproto-dpif: Differentiate between different miss types in packet in
    
    Replace the generated_by_table_miss field of struct ofproto_packet_in
    with a miss_type field.
    
    The generated_by_table_miss field allowed packet-in messages generated
    by table-miss rules to be differentiated. This differentiation
    is still provided for by miss_type being set to OFPROTO_PACKET_IN_MISS_FLOW.
    
    This patch allows further differentiation by setting miss_type
    to OFPROTO_PACKET_IN_MISS_WITHOUT_FLOW if the packet-in message
    is generated by a table-miss which is not handled by a table-miss rule.
    
    This is in preparation for OpenFlow 1.3 version-specific
    handling of the default action for such misses.
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
