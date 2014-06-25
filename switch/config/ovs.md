---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
dd523a21-365d-4241-95ff-3552d18a9d9f
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
_uuid               : ebced452-de87-40b8-bea0-0d35bcc1f518
controller          : [e93d3116-dc7d-4258-8d1e-7ee77585dd81]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [06d2238b-3bb5-4694-8d60-a260ac35bfdd, 094d18e0-8f1e-4bb9-a6ef-0ebbc69828ab, 3051cd98-1e8d-461d-881a-1ca11f21bb48, 8bd39eae-e287-4caf-8b32-c284ebd111f3]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e93d3116-dc7d-4258-8d1e-7ee77585dd81
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=657, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3051cd98-1e8d-461d-881a-1ca11f21bb48
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5de1568b-7050-44b5-a0f7-10e21ccb3fc0]
name                : eth23

_uuid               : 094d18e0-8f1e-4bb9-a6ef-0ebbc69828ab
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aa0a1787-97b1-4026-af0e-e9aa59a79a70]
name                : eth21

_uuid               : 8bd39eae-e287-4caf-8b32-c284ebd111f3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [171334ed-ae4d-4f15-81ce-4b37c3203d46]
name                : br0

_uuid               : 06d2238b-3bb5-4694-8d60-a260ac35bfdd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a407eb7f-688a-4a4b-af71-6fe786bac249]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 171334ed-ae4d-4f15-81ce-4b37c3203d46
admin_state         : down
ifindex             : 721
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 5de1568b-7050-44b5-a0f7-10e21ccb3fc0
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2957843784, tx_dropped=0, tx_errors=0, tx_packets=13425826}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : aa0a1787-97b1-4026-af0e-e9aa59a79a70
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
statistics          : {collisions=0, rx_bytes=901520094, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=92369713, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a407eb7f-688a-4a4b-af71-6fe786bac249
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2848733292, tx_dropped=0, tx_errors=0, tx_packets=36313827}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 26a5075bb6a0c96a94ea5be7672185a2a8f3eedc
Author:     Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
AuthorDate: Wed Jun 25 11:39:34 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Wed Jun 25 14:35:50 2014 -0700

    dpif-netdev: delete lost packets in dp_execute_cb&#40;&#41;
    
    This commit fixes memory leaks in dp_execute_cb&#40;&#41; in two cases:
        - when the output port cannot be found
        - when the recirculation depth is exceeded
    
    Reported-by: Pravin Shelar &lt;pshelar@nicira.com&gt;
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
