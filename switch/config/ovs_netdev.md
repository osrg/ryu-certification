---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4603aae2-d3fc-400c-af39-adf2a71450ea
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
_uuid               : 18f83568-eed4-45dc-a5f7-9f15a2d9bb57
controller          : [75b0389e-98bc-4768-bc75-821357f49c1f]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1164a6cf-9b48-4819-be8d-67d58d35f70c, 271b0ab5-64b5-4b1f-831b-adfb067c7b83, f37f2e05-0e89-4032-8e04-78f59f1128b6, fdb10a41-9ca5-40a1-82e0-22f0565f40ee]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 75b0389e-98bc-4768-bc75-821357f49c1f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=697, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : fdb10a41-9ca5-40a1-82e0-22f0565f40ee
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [853a2715-490d-4d62-9ca4-d4abbfdf4535]
name                : eth22

_uuid               : 271b0ab5-64b5-4b1f-831b-adfb067c7b83
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [353cfa2a-8e6b-4884-9485-f1add5affdd2]
name                : eth23

_uuid               : f37f2e05-0e89-4032-8e04-78f59f1128b6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [965c9eb9-9dff-4d4e-8c4e-6e141dab9846]
name                : br0

_uuid               : 1164a6cf-9b48-4819-be8d-67d58d35f70c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8a70554c-293d-4749-baa9-04afe305a0a6]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8a70554c-293d-4749-baa9-04afe305a0a6
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
statistics          : {collisions=0, rx_bytes=3642061145, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=171464791, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 965c9eb9-9dff-4d4e-8c4e-6e141dab9846
admin_state         : down
duplex              : full
ifindex             : 298
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

_uuid               : 853a2715-490d-4d62-9ca4-d4abbfdf4535
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3107597934, tx_dropped=0, tx_errors=0, tx_packets=105196722}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 353cfa2a-8e6b-4884-9485-f1add5affdd2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=296279112, tx_dropped=0, tx_errors=0, tx_packets=8787454}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 42767cce7247bf609ab4a06bcbb3cdc480776cc2
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Wed Oct 29 09:59:57 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Wed Oct 29 09:59:57 2014 -0700

    tests/test-classifier: Properly use ovsrcu_postpone.
    
    Following patches add stricter checks of RCU memory management of
    rules removed from a classifier.  This patch properly postpones
    freeing of 'struct cls_rule's that have been removed from a
    classifier.
    
    Also remove all the rules from classifier before destructing it in
    test_rule_replacement&#40;&#41;.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
