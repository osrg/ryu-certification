---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fc97de16-ed72-4a52-88c7-6b105df141f0
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a5b545ff-6e5c-4b33-aa29-87e2e9e2172d
controller          : [c0e12416-3be2-47ba-9ebf-c63ac4b7295c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1ee4ce10-7af1-46ec-bc3d-124b11c4d678, 6834d7be-41e4-4757-a7bc-455a2563a923, 6ae2ccf1-2203-4f1d-87ba-0542585793f3, e453d9c7-e851-458d-8ae4-85e56ca46be5]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c0e12416-3be2-47ba-9ebf-c63ac4b7295c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=662, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1ee4ce10-7af1-46ec-bc3d-124b11c4d678
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [50d42df9-debf-44d8-a01d-cef1f8087024]
name                : eth22

_uuid               : 6ae2ccf1-2203-4f1d-87ba-0542585793f3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8aebd578-10ee-447d-be5a-dfad08c0eea0]
name                : br0

_uuid               : 6834d7be-41e4-4757-a7bc-455a2563a923
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8a4c07c5-ea5e-4427-87f7-16aed36465b0]
name                : eth21

_uuid               : e453d9c7-e851-458d-8ae4-85e56ca46be5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2baad6eb-ad0c-410c-83be-5aa3b7fee5d4]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8aebd578-10ee-447d-be5a-dfad08c0eea0
admin_state         : down
duplex              : full
ifindex             : 37
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

_uuid               : 50d42df9-debf-44d8-a01d-cef1f8087024
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=289500232, tx_dropped=0, tx_errors=0, tx_packets=194560}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8a4c07c5-ea5e-4427-87f7-16aed36465b0
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
statistics          : {collisions=0, rx_bytes=677944092, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=455288, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2baad6eb-ad0c-410c-83be-5aa3b7fee5d4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=523962000, tx_dropped=0, tx_errors=0, tx_packets=349308}
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
