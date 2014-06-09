---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
54cabfbf-3a9a-4d0a-a60c-10097af45865
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0fca48e1-2c49-4886-b100-bf931447203b
controller          : [7debd499-80ec-416a-98ec-7e897cd52377]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [81ef42d1-f9a1-4c97-9ab7-8ab0531c33fe, 90d5d5b5-b8b3-40f3-80f0-49fd89f00766, d2d2f9c8-ec83-420b-afe9-906bb197b504, f6053215-3131-430b-a292-349a86ed3157]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7debd499-80ec-416a-98ec-7e897cd52377
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=967, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d2d2f9c8-ec83-420b-afe9-906bb197b504
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c457a7cc-e511-485d-bd47-a592020f6b97]
name                : eth23

_uuid               : 81ef42d1-f9a1-4c97-9ab7-8ab0531c33fe
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7f370912-7618-4871-9a70-db3ea39052ae]
name                : eth21

_uuid               : f6053215-3131-430b-a292-349a86ed3157
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [676c3494-39f4-41a9-9b5b-c35a03aab8ae]
name                : eth22

_uuid               : 90d5d5b5-b8b3-40f3-80f0-49fd89f00766
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b1a3ceb4-18c7-4b0a-96d7-aa42501673be]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b1a3ceb4-18c7-4b0a-96d7-aa42501673be
admin_state         : down
duplex              : full
ifindex             : 410
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

_uuid               : 676c3494-39f4-41a9-9b5b-c35a03aab8ae
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1082547690, tx_dropped=0, tx_errors=0, tx_packets=12197627}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c457a7cc-e511-485d-bd47-a592020f6b97
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1118599408, tx_dropped=0, tx_errors=0, tx_packets=6472356}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 7f370912-7618-4871-9a70-db3ea39052ae
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
statistics          : {collisions=0, rx_bytes=4256149412, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=25806458, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c1223b11d498b66f27c889f4438ad88394299fc0
Author:     Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
AuthorDate: Tue Jun 3 11:29:53 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Jun 9 11:28:59 2014 -0700

    acinclude.m4: dpdk: link with -ldl if necessary
    
    On some systems libintel_dpdk.a fails to link with libopenvswitch
    unless -ldl is used. This should address the issue
    
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
