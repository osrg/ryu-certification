---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
993461cb-62e6-40b8-aceb-208988e39eb1
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0978fda1-8dff-4960-bca8-c58e284c6665
controller          : [25eb5cdc-2a79-4c4b-af78-fa7a18bec21c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [086050d6-3fad-47ed-a4fa-f8783db7820d, 4ec8beb0-29f8-4f5d-a919-47586d57571a, ba817c43-fb49-403d-9a69-41ca978bf111, d6cfdebb-bf35-4744-a81e-41b7d61f4d8b]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 25eb5cdc-2a79-4c4b-af78-fa7a18bec21c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=691, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4ec8beb0-29f8-4f5d-a919-47586d57571a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3ff17d04-e51d-425a-b213-c82e06ced7ba]
name                : br0

_uuid               : 086050d6-3fad-47ed-a4fa-f8783db7820d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [413b342e-bfec-478b-91e0-20c30396e600]
name                : eth22

_uuid               : ba817c43-fb49-403d-9a69-41ca978bf111
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [eeb5e037-d61d-4a36-a484-cfdb189b4bf2]
name                : eth21

_uuid               : d6cfdebb-bf35-4744-a81e-41b7d61f4d8b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f11e6ef4-8af7-4f10-a7a3-724e0d734994]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f11e6ef4-8af7-4f10-a7a3-724e0d734994
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3826447408, tx_dropped=0, tx_errors=0, tx_packets=8277588}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3ff17d04-e51d-425a-b213-c82e06ced7ba
admin_state         : down
duplex              : full
ifindex             : 281
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

_uuid               : 413b342e-bfec-478b-91e0-20c30396e600
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2624104352, tx_dropped=0, tx_errors=0, tx_packets=104871851}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : eeb5e037-d61d-4a36-a484-cfdb189b4bf2
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
statistics          : {collisions=0, rx_bytes=2601722993, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=170765774, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3a17f00f784b4b47917f336ca19bdc7078faade5
Author:     Alin Serdean &lt;aserdean@cloudbasesolutions.com&gt;
AuthorDate: Thu Oct 23 23:38:21 2014 +0000
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Oct 24 08:58:57 2014 -0700

    datapath-windows: Avoid BSOD when no event queue found.
    
    kd&gt; ??instance
    struct _OVS_OPEN_INSTANCE * 0xffffe00002c59f20 _FILE_OBJECT
       +0x010 eventQueue       : &#40;null&#41;
       +0x018 packetQueue      : 0xffffe00003ad83f0 - 0xffffe0002876eb18 fffff8012876eb20 fffff8012876eb80 fffff8012876f290 fffff8012876f2d0 fffff8012876f410 fffff8002876f5a0 fffff8002876f610 fffff8002876f660 fffff8002876f6b0 fffff8002876f840 fffff8012876f870 fffff8012876fa20 fffff8012876fa90 00000000010feef8 00000000010fef00 00000000010fefb0 00000000010ff000 00007ff8010ff540 00007ff8010ff5b0 000000002876f640
       +0x000 cookie           : 0x3a9ae28
       +0x004 dpNo             : 0
    SYMBOL_STACK_INDEX:  6
    
    SYMBOL_NAME:  OVSExt!OvsWaitEventIoctl+116
    
    FOLLOWUP_NAME:  MachineOwner
    
    MODULE_NAME: OVSExt
    
    IMAGE_NAME:  OVSExt.sys
    
    DEBUG_FLR_IMAGE_TIMESTAMP:  54498bc5
    
    BUCKET_ID_FUNC_OFFSET:  116
    
    FAILURE_BUCKET_ID:  AV_OVSExt!OvsWaitEventIoctl
    
    BUCKET_ID:  AV_OVSExt!OvsWaitEventIoctl
    
    ANALYSIS_SOURCE:  KM
    
    FAILURE_ID_HASH_STRING:  km:av_ovsext!ovswaiteventioctl
    
    FAILURE_ID_HASH:  {07550bfb-c3b5-0412-b95d-f89a5c4671a9}
    
    Signed-off-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Acked-by: Eitan Eliahu &lt;eliahue@vmware.com&gt;
    Acked-by: Sorin Vinturis &lt;svinturis@cloudbasesolutions.com&gt;
    Acked-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
