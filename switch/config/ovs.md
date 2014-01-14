---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4ac15c12-bf5f-4ea2-abc5-83a0ac1027d8
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 310f3d1a-7e9a-4dff-a5da-038c7d265936
controller          : [b08e030e-9dec-4e47-9628-668ac606d7ec]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [312d756f-2dd3-427e-9216-c9c9ac98fe8f, 8669a2a3-3ded-4cd2-9f94-b2db8fb2d32f, b6f9ecd1-e009-4966-a2d3-817960e07c27]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b08e030e-9dec-4e47-9628-668ac606d7ec
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b6f9ecd1-e009-4966-a2d3-817960e07c27
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [eb34012f-ce65-415f-860b-b548338f9a6f]
name                : br0

_uuid               : 312d756f-2dd3-427e-9216-c9c9ac98fe8f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3716f11d-ef8b-4379-be86-e7b5d7a4a471]
name                : eth7

_uuid               : 8669a2a3-3ded-4cd2-9f94-b2db8fb2d32f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [924fa1cf-4861-4284-9bfd-4bc0221e4dc0]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3716f11d-ef8b-4379-be86-e7b5d7a4a471
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
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : eb34012f-ce65-415f-860b-b548338f9a6f
admin_state         : up
ifindex             : 69
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 924fa1cf-4861-4284-9bfd-4bc0221e4dc0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
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
