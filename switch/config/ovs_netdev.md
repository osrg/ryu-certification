---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3d1a8877-10fb-4bae-85d5-245255ee5636
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 05116198-6e7f-4e9e-85a7-a4be937e9b44
controller          : [aa873373-7be7-4534-9211-24b720f10078]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [6b651853-7b14-446f-a864-59de6a976233, 6f4cc232-d086-4ac1-afdc-117ceaf36397, 91a639ca-cdd5-4f39-b634-5dff1c4a6957, b1f25004-5c71-44ee-9fe5-3e59e53be9e6]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : aa873373-7be7-4534-9211-24b720f10078
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=977, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b1f25004-5c71-44ee-9fe5-3e59e53be9e6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c30ab70e-2b92-487b-8c53-06313c664694]
name                : br0

_uuid               : 6f4cc232-d086-4ac1-afdc-117ceaf36397
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [81a0427d-9da4-4a54-bb11-0f28d50c0822]
name                : eth22

_uuid               : 91a639ca-cdd5-4f39-b634-5dff1c4a6957
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [352385f0-52d9-4db4-8a8d-01c455fa1e98]
name                : eth23

_uuid               : 6b651853-7b14-446f-a864-59de6a976233
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9c8139c0-21b6-4abc-aeaf-c809a30d8f1e]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 352385f0-52d9-4db4-8a8d-01c455fa1e98
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=315833080, tx_dropped=0, tx_errors=0, tx_packets=8801174}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9c8139c0-21b6-4abc-aeaf-c809a30d8f1e
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
statistics          : {collisions=0, rx_bytes=3270674811, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=36632587, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 81a0427d-9da4-4a54-bb11-0f28d50c0822
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=428273025, tx_dropped=0, tx_errors=0, tx_packets=20364814}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c30ab70e-2b92-487b-8c53-06313c664694
admin_state         : down
duplex              : full
ifindex             : 541
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6ddb63134def5509640e5b7713eea39095e1d17f
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Mon Jun 16 12:45:04 2014 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Thu Jun 19 18:29:25 2014 -0700

    datapath: keep mask array compact when deleting mask
    
    When deleting a mask from the mask array, we always move the last entry
    into its current location. Another approach can be NULL in its
    current place, and periodically compact it.
    
    The approach taken by this patch is more efficient during run
    time.  During look up, fast path packet don't have to skip over NULL
    pointers.
    
    A more important advantage of this approach is that it tries to
    keep the mask array index stable by avoiding periodic index
    reshuffle.
    
    This patch implements an optimization to further promote index
    stability.  By leaving the last entry value intact when moving it
    to a new location, the old cache index can 'fix' themselves, by noticing
    the index in the cache is outside the valid mask array region. The
    new index can be found by scanning the mask pointer within the valid
    rtegion.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
