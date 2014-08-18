---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ba551290-0977-4cfd-b5c9-055fe6abf29b
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 98270b5d-c2dd-4fc6-addb-ccf93956fb20
controller          : [9e928110-2a76-4ae0-9abc-8096bd50ecdc]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2e151d61-1361-4b12-b6be-899887213b8c, 9d212a1a-d13f-4c3f-8469-ebdd53b3c139, a4535dfd-a40a-43ad-ac47-0427d32b2ad1, bc427272-9c6a-41fc-a3e2-157248eeb7ec]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9e928110-2a76-4ae0-9abc-8096bd50ecdc
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=662, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a4535dfd-a40a-43ad-ac47-0427d32b2ad1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1d01048f-ccf9-4dc2-b6dd-f43a38fe866f]
name                : eth21

_uuid               : 2e151d61-1361-4b12-b6be-899887213b8c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [15102d3e-f513-43e2-b919-43d20e642b3b]
name                : eth23

_uuid               : 9d212a1a-d13f-4c3f-8469-ebdd53b3c139
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c85c5afd-ddb3-4ac9-8ded-12133d035b60]
name                : br0

_uuid               : bc427272-9c6a-41fc-a3e2-157248eeb7ec
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b2f8a666-38a4-4f13-856d-a2ffaa9c8339]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c85c5afd-ddb3-4ac9-8ded-12133d035b60
admin_state         : down
duplex              : full
ifindex             : 33
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

_uuid               : 15102d3e-f513-43e2-b919-43d20e642b3b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=325111500, tx_dropped=0, tx_errors=0, tx_packets=216741}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b2f8a666-38a4-4f13-856d-a2ffaa9c8339
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=207895412, tx_dropped=0, tx_errors=0, tx_packets=139571}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 1d01048f-ccf9-4dc2-b6dd-f43a38fe866f
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
statistics          : {collisions=0, rx_bytes=444211676, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=298204, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1ef49150ab78f1f859bd875ce3ce7fcec778554c
Author:     Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
AuthorDate: Mon Aug 18 12:57:42 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Aug 18 13:17:34 2014 -0700

    fat-rwlock: fat_rwlock_tryrdlock&#40;&#41; should never block
    
    fat_rwlock_tryrdlock&#40;&#41; used to call fat_rwlock_get_slot__&#40;&#41; which could block
    in the &quot;slow path&quot; case. This commit adds fat_rwlock_try_get_slot__&#40;&#41; which
    does not block, even in the &quot;slow path&quot; case.
    
    This fixes a minor issue in dpif-netdev: when the datapath has no registered
    upcall handler &#40;e.g. if it is created with dpctl commands&#41;, dp_netdev_input&#40;&#41;
    hangs if it does not find a packet's flow in the classifier.  This is
    because dpif-netdev uses its upcall_rwlock as a way to enable and disable
    upcalls and thus holds the upcall_rwlock write lock as long as upcalls are
    disabled.  Both holding the write lock and creating a slot require the
    fat_rwlock's mutex, causing the hang.
    
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
