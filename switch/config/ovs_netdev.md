---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
02836d87-5a3e-408c-879b-b25666623543
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d16731a3-94b5-4ac5-9d02-eb244b8a3fd0
controller          : [32a34c3d-ab90-4750-b0fa-791aab35da43]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [356de824-1063-43f1-af8b-8fe6c3e4d19a, 3cff11f8-d59d-4925-b94a-99bd3210bf8d, 5483bde9-2063-43d3-bd26-726a0902e324]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 32a34c3d-ab90-4750-b0fa-791aab35da43
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=372, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 356de824-1063-43f1-af8b-8fe6c3e4d19a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2dfda494-7816-46ee-a8b8-3c02a753811d]
name                : br0

_uuid               : 3cff11f8-d59d-4925-b94a-99bd3210bf8d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [879154a3-825a-4202-bd72-abf9a13275ad]
name                : eth7

_uuid               : 5483bde9-2063-43d3-bd26-726a0902e324
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [428b16b9-1d97-4300-8ff0-091cb2e802a6]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2dfda494-7816-46ee-a8b8-3c02a753811d
admin_state         : up
duplex              : full
ifindex             : 291
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

_uuid               : 428b16b9-1d97-4300-8ff0-091cb2e802a6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2399440, tx_dropped=0, tx_errors=0, tx_packets=25619}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 879154a3-825a-4202-bd72-abf9a13275ad
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
statistics          : {collisions=0, rx_bytes=3058776848, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72589696, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit da695497b81f40f60b93116d4bfbf37505b7677c
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed Jan 15 12:59:16 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Feb 19 14:50:57 2014 -0800

    netdev: Change netdev_class_rwlock to recursive mutex, for POSIX safety.
    
    With glibc, rwlocks by default allow recursive read-locking even if a
    thread is blocked waiting for the write-lock.  POSIX allows such attempts
    to deadlock, and it appears that the libc used in NetBSD, at least, does
    deadlock.  The netdev_class_rwlock is in fact acquired recursively in this
    way, which is a bug.  This commit fixes the problem by switching to a
    recursive mutex.  This allows for less parallelism, but according to an
    existing comment that doesn't matter here anyway.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
