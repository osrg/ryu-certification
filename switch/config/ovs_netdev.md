---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
16b500e5-9e16-49f5-b04a-d73d2cd2a5e1
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 2b6289d1-383c-4e40-9772-5ad799b299d9
controller          : [8fc63517-bcf9-4ccb-87e7-f69a629739cd]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [aec5b4d4-743c-4297-81f3-723c3162e541, b717e67c-d1df-454a-91a0-7c4a7de30d15, d286dd21-8162-4468-ae5d-f11612cc7640]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8fc63517-bcf9-4ccb-87e7-f69a629739cd
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=302, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : aec5b4d4-743c-4297-81f3-723c3162e541
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5d91436c-51e8-4f7a-9ce9-3d3b39c3d671]
name                : eth7

_uuid               : b717e67c-d1df-454a-91a0-7c4a7de30d15
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [02b9be74-6290-45f9-9316-973d2fb279f0]
name                : br0

_uuid               : d286dd21-8162-4468-ae5d-f11612cc7640
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5df38908-2774-42df-b63b-8e1aadebe12f]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 5df38908-2774-42df-b63b-8e1aadebe12f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=449284, tx_dropped=0, tx_errors=0, tx_packets=4840}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 5d91436c-51e8-4f7a-9ce9-3d3b39c3d671
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
statistics          : {collisions=0, rx_bytes=1435830, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=14520, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 02b9be74-6290-45f9-9316-973d2fb279f0
admin_state         : up
duplex              : full
ifindex             : 71
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
commit 06f81620436881449cb9a2db4f875aa00803f28d
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Mon Jan 13 11:21:12 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Jan 14 14:45:10 2014 -0800

    classifier: Use fat_rwlock instead of ovs_rwlock.
    
    Jarno Rajahalme reported up to 40% performance gain on netperf TCP_CRR with
    an earlier version of this patch in combination with a kernel NUMA patch,
    together with a reduction in variance:
        http://openvswitch.org/pipermail/dev/2014-January/035867.html
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
