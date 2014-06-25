---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
5d67ca31-33cf-4fc8-b8ee-e0fde5b9ead8
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 426754a4-0cb2-45fa-b595-6f80d0e3f440
controller          : [ea816152-1d1a-42b4-bbae-2c55d1ee7e1f]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [6079fb26-e3e8-408e-ac8a-8707b2257624, d1643480-7420-4440-9fb2-a8429a746cd6, d73abada-3e05-4410-9e6f-534a141e1169, de4f9454-eb00-43b2-9b51-01dd2a82be8e]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ea816152-1d1a-42b4-bbae-2c55d1ee7e1f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=971, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : de4f9454-eb00-43b2-9b51-01dd2a82be8e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [52c18b47-9af8-431b-8b63-78c2d26a71af]
name                : eth22

_uuid               : d1643480-7420-4440-9fb2-a8429a746cd6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2b322793-3c6c-40bd-b137-bc3690049c42]
name                : eth23

_uuid               : 6079fb26-e3e8-408e-ac8a-8707b2257624
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a409c0aa-f094-439c-b248-62584c2f3887]
name                : br0

_uuid               : d73abada-3e05-4410-9e6f-534a141e1169
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2e8f980f-a6a2-424c-b531-13be0ba2b530]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a409c0aa-f094-439c-b248-62584c2f3887
admin_state         : down
ifindex             : 714
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

_uuid               : 2b322793-3c6c-40bd-b137-bc3690049c42
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2610688284, tx_dropped=0, tx_errors=0, tx_packets=13194389}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2e8f980f-a6a2-424c-b531-13be0ba2b530
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
statistics          : {collisions=0, rx_bytes=445623220, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=92063490, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 52c18b47-9af8-431b-8b63-78c2d26a71af
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2669922550, tx_dropped=0, tx_errors=0, tx_packets=36193548}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5715de1400dd1fafe7d3d08a02c6ca0a0cd998e9
Author:     Ryan Wilson &lt;wryan@nicira.com&gt;
AuthorDate: Wed Jun 25 13:05:17 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jun 25 13:26:05 2014 -0700

    dpif-netdev: Fix memory leak in dpif_netdev_flow_put&#40;&#41;
    
    miniflow_destroy&#40;&#41; needs to be called after using miniflow_init&#40;&#41;.
    Otherwise, if the miniflow mallocs data, then a memory leak may
    occur.
    
    Found by inspection.
    
    Signed-off-by: Ryan Wilson &lt;wryan@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
