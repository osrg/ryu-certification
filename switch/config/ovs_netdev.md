---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
33a97dfe-230e-4ff3-8053-d45c520ac8df
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
_uuid               : eaf92cc2-0645-400c-9c55-aa8d09c6359d
controller          : [67eb3734-0c25-4f65-810f-ca5e5cde9733]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2d6556ad-8646-425c-b4a9-1656d413eb00, 2d9b5732-e20f-4616-b9dc-b65ef0ef76fc, 365b95de-db87-4031-98de-d1da7147f21e, f98f348e-80af-4cfa-bbb6-2a5d03f95d53]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 67eb3734-0c25-4f65-810f-ca5e5cde9733
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=682, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2d6556ad-8646-425c-b4a9-1656d413eb00
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a2689e7f-2041-4880-b725-e782c155af16]
name                : eth21

_uuid               : f98f348e-80af-4cfa-bbb6-2a5d03f95d53
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5e6fdb93-c215-41c7-b5a9-4f404aa39bdc]
name                : eth22

_uuid               : 365b95de-db87-4031-98de-d1da7147f21e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [488c213a-c678-4032-af62-e331d45d572d]
name                : br0

_uuid               : 2d9b5732-e20f-4616-b9dc-b65ef0ef76fc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [98e3a99d-a6da-47a7-ae8d-e23935476fe3]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 98e3a99d-a6da-47a7-ae8d-e23935476fe3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3028199204, tx_dropped=0, tx_errors=0, tx_packets=4882111}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 488c213a-c678-4032-af62-e331d45d572d
admin_state         : down
duplex              : full
ifindex             : 176
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

_uuid               : 5e6fdb93-c215-41c7-b5a9-4f404aa39bdc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2623417542, tx_dropped=0, tx_errors=0, tx_packets=47586606}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a2689e7f-2041-4880-b725-e782c155af16
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
statistics          : {collisions=0, rx_bytes=958501149, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=75139618, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6db454dc00fa5d9693ebdf6c5e10c61030f8df8e
Author:     Simon Horman &lt;simon.horman@netronome.com&gt;
AuthorDate: Wed Sep 24 12:41:02 2014 +0000
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Wed Sep 24 14:00:15 2014 -0700

    ofproto-dpif-rid: correct logic error in rid_pool_alloc_id&#40;&#41;
    
    When searching through the valid ids an id should
    be used if is not found rather than if it is found.
    
    It appears to me that without this change duplicate recirculation
    ids may used in cases where the last recirculation id has
    been allocated; selection loops back to the beginning of the pool and;
    reaches a recirculation id that is still in use.
    
    As the number of recirculation ids is currently RECIRC_ID_N_IDS = 1024 this
    does not seem beyond the bounds of possibility.
    
    I have not verified that such a scenario can actually occur.  But it seems
    that a likely consequence would be that some packets may be forwarded
    incorrectly.
    
    Signed-off-by: Simon Horman &lt;simon.horman@netronome.com&gt;
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
