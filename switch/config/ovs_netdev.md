---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
49bebde4-ff88-4964-9c70-8e8d9ce8bbe7
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
_uuid               : 25c75434-99e8-44b5-a413-c45fa7f2b080
controller          : [a46c5ca0-e877-467c-b57a-0d681926cb5c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [127090db-d056-4d2d-b138-f8ff2e5544b9, 7e10ee0b-5899-437b-b268-8cb21d122847, c7deaceb-14e5-403c-a686-5fcfe7ca35d1]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a46c5ca0-e877-467c-b57a-0d681926cb5c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=372, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 127090db-d056-4d2d-b138-f8ff2e5544b9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0f433b73-6e5c-47fa-963a-b0f0898eb336]
name                : eth7

_uuid               : 7e10ee0b-5899-437b-b268-8cb21d122847
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f880816f-49f6-435e-b125-a029412fc06f]
name                : eth8

_uuid               : c7deaceb-14e5-403c-a686-5fcfe7ca35d1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0a227420-c2e4-4a93-b794-8a26a1f933d2]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0a227420-c2e4-4a93-b794-8a26a1f933d2
admin_state         : up
duplex              : full
ifindex             : 296
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

_uuid               : 0f433b73-6e5c-47fa-963a-b0f0898eb336
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
statistics          : {collisions=0, rx_bytes=3058915663, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72591100, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : f880816f-49f6-435e-b125-a029412fc06f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2442292, tx_dropped=0, tx_errors=0, tx_packets=26075}
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
