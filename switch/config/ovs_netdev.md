---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3ede047d-0713-4857-a207-4dd38a3943c8
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7e2a6239-0485-4bbf-8c5f-85dcb895864e
controller          : [a9ef3e94-a2aa-4a3c-812f-16ff6feeeec5]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [28d5849c-fa09-401d-8ecc-f2e2feaa5b86, 401303f7-23ae-4992-a009-bd4cb8455afd, 6fdfd8a5-93f0-4f18-967a-a36d2ca83eb5, a148541e-d9c2-48f8-8c4d-3ead085f5ee3]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a9ef3e94-a2aa-4a3c-812f-16ff6feeeec5
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=692, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 28d5849c-fa09-401d-8ecc-f2e2feaa5b86
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5f96796c-ea1d-4610-b80b-a4403918d766]
name                : eth23

_uuid               : 6fdfd8a5-93f0-4f18-967a-a36d2ca83eb5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4640d84c-3d46-40bb-9664-34d47de0480d]
name                : eth22

_uuid               : a148541e-d9c2-48f8-8c4d-3ead085f5ee3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bb9d1574-5eed-4db0-a65a-07efa7c779a7]
name                : eth21

_uuid               : 401303f7-23ae-4992-a009-bd4cb8455afd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7adc8298-6f24-4a64-bd04-a61aab92acb9]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 5f96796c-ea1d-4610-b80b-a4403918d766
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=713894204, tx_dropped=0, tx_errors=0, tx_packets=3339241}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 4640d84c-3d46-40bb-9664-34d47de0480d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3307935892, tx_dropped=0, tx_errors=0, tx_packets=45171673}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 7adc8298-6f24-4a64-bd04-a61aab92acb9
admin_state         : down
duplex              : full
ifindex             : 126
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

_uuid               : bb9d1574-5eed-4db0-a65a-07efa7c779a7
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
statistics          : {collisions=0, rx_bytes=2570768570, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=64743687, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9c7e020fd60baa98528bd202caeb9e908b036216
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Tue Sep 9 11:01:52 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Fri Sep 12 10:26:56 2014 -0700

    ovs-rcu: Make ovsrcu_quiesce&#40;&#41; flush the callback event set.
    
    On current master, the per-thread callback event set is flushed
    when ovsrcu_quiesce_start&#40;&#41; is called or when the callback
    event set is full.  For threads that only call 'ovsrcu_quiesce&#40;&#41;'
    to indicate quiescient state, their callback event set will not
    be flushed for execution until the set is full.  And this could
    take a very long time.
    
    Theoretically, this should not be an issue, since rcu postponed
    callback events should only free the old version of objects.
    However, current ovs does not follow this rule, and some callback
    events include other activities like unregistering the netdev
    from global name-netdev map.  The delay of unregistering the netdev
    &#40;by threads that only calls ovsrcu_quiesce&#40;&#41;&#41; will prevent the
    recreate of same netdev indefinitely.
    
    As a short-term workaround, this commit makes every call to
    ovsrcu_quiesce&#40;&#41; flush the callback event set.  In the long run,
    there will be a refactor of the use of ovs-rcu module, in which all
    callback events only free the old version of objects.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
