---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
550b04d6-673b-45b7-a74c-82c90dde0438
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 67c2a30d-a769-482b-80f5-04b9902dfd6a
controller          : [89d45805-bb1f-4897-bd9a-84005bbf52cc]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0ea8eeea-e9dd-46d9-bf97-4036b6fd4fb7, 144a89e6-5c6f-429c-ac00-40d1503ddfa7, 47fa0911-78e9-41fa-b1b0-2e1c06d6bbca, ef67636e-5041-4c08-ad30-a13559201d83]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 89d45805-bb1f-4897-bd9a-84005bbf52cc
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=667, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 47fa0911-78e9-41fa-b1b0-2e1c06d6bbca
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e31b67a6-9113-495c-a633-a314a41e36dc]
name                : eth22

_uuid               : 144a89e6-5c6f-429c-ac00-40d1503ddfa7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4cde262d-2001-4bb0-9cf0-6998d5041cd8]
name                : br0

_uuid               : 0ea8eeea-e9dd-46d9-bf97-4036b6fd4fb7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [43870cc0-c10c-4959-8722-cbc0862ecf5a]
name                : eth21

_uuid               : ef67636e-5041-4c08-ad30-a13559201d83
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ec15a139-dacb-4fa5-b474-6d4106ece845]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 43870cc0-c10c-4959-8722-cbc0862ecf5a
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
statistics          : {collisions=0, rx_bytes=561073384, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=376743, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 4cde262d-2001-4bb0-9cf0-6998d5041cd8
admin_state         : down
duplex              : full
ifindex             : 35
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

_uuid               : ec15a139-dacb-4fa5-b474-6d4106ece845
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=424395000, tx_dropped=0, tx_errors=0, tx_packets=282930}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e31b67a6-9113-495c-a633-a314a41e36dc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=248836572, tx_dropped=0, tx_errors=0, tx_packets=167158}
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
