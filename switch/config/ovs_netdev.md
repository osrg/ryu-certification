---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fb255a00-a19a-4a66-845b-9a4a042509d3
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 4fb3a5e9-9337-4b48-b8ab-2334ed7ad45d
controller          : [96f0bc6b-f8f2-4001-8a63-034017d17ea4]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [04c3db3f-e6ac-4fa3-983e-91ed40336683, 6ab1f852-624a-493e-857d-c7747976a79f, 72e7ca0f-7093-48ba-86f5-910e95175ae8, c789ffaa-3748-4030-b7ee-a6694beb82b0]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 96f0bc6b-f8f2-4001-8a63-034017d17ea4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=547, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6ab1f852-624a-493e-857d-c7747976a79f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [50c4600c-fbef-49f4-aa8e-6a109b727a80]
name                : eth21

_uuid               : c789ffaa-3748-4030-b7ee-a6694beb82b0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bd82610d-f03d-40b4-aa21-1ac6bd3a339a]
name                : eth22

_uuid               : 04c3db3f-e6ac-4fa3-983e-91ed40336683
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [33abacfd-cfaa-4143-9a95-cd52959ca263]
name                : br0

_uuid               : 72e7ca0f-7093-48ba-86f5-910e95175ae8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [533037b6-7440-4f4c-b3ee-89dc6c8b989a]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 50c4600c-fbef-49f4-aa8e-6a109b727a80
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
statistics          : {collisions=0, rx_bytes=3515378089, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2359425, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : bd82610d-f03d-40b4-aa21-1ac6bd3a339a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1435306210, tx_dropped=0, tx_errors=0, tx_packets=962709}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 33abacfd-cfaa-4143-9a95-cd52959ca263
admin_state         : down
duplex              : full
ifindex             : 188
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

_uuid               : 533037b6-7440-4f4c-b3ee-89dc6c8b989a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2399065500, tx_dropped=0, tx_errors=0, tx_packets=1599377}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0b810ca89262d0ff270994a5074d29e3c0b0002a
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Wed May 14 19:53:51 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Wed May 14 19:53:51 2014 -0700

    lib/classifier: Simpilify array ordering.
    
    The terminology we used for subtable ordering &#40;'splice', 'right
    before'&#41; was inherited from an earlier use of a linked list, and
    turned out to be confusing when applied to an array.  Also, we only
    ever move one subtable earlier or later within the array, so we can
    simplify the code as well.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
