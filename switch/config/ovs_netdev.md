---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
013d0936-d118-4d7e-9199-1138e3f327f4
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 1ff8a1f4-c3af-4ec0-ac30-d5c3b4e7ae7a
controller          : [a94a3826-b2bb-4246-89c9-b1c0a8c6482f]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [939a8c5c-33ad-42d1-8eb1-ee590fd05996, a0fce1e3-9b9e-4508-b05d-968662960205, b4f97e98-4493-4ab4-a081-4034cb50f5a4, fb284e09-8583-42bb-ac25-45060ae7e042]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a94a3826-b2bb-4246-89c9-b1c0a8c6482f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=1002, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b4f97e98-4493-4ab4-a081-4034cb50f5a4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a9976dd1-27b1-4137-bb38-d335203b8402]
name                : br0

_uuid               : 939a8c5c-33ad-42d1-8eb1-ee590fd05996
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d5129d8d-a88e-42dd-9416-033267d68e2a]
name                : eth22

_uuid               : fb284e09-8583-42bb-ac25-45060ae7e042
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8b002a7c-5a4f-4247-b06a-1c72759ff758]
name                : eth21

_uuid               : a0fce1e3-9b9e-4508-b05d-968662960205
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d9a35fab-6ac3-402c-8766-c7c35f82bf66]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8b002a7c-5a4f-4247-b06a-1c72759ff758
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
statistics          : {collisions=0, rx_bytes=463896141, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=6074597, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d5129d8d-a88e-42dd-9416-033267d68e2a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3585878976, tx_dropped=0, tx_errors=0, tx_packets=2404227}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a9976dd1-27b1-4137-bb38-d335203b8402
admin_state         : down
duplex              : full
ifindex             : 292
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

_uuid               : d9a35fab-6ac3-402c-8766-c7c35f82bf66
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2465049704, tx_dropped=0, tx_errors=0, tx_packets=4506678}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3c27dbe6b71e36c0d05e8299e811615697fc1bc0
Author:     Ryan Wilson &lt;wryan@nicira.com&gt;
AuthorDate: Thu May 29 14:56:09 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Thu May 29 14:59:37 2014 -0700

    route-table: Make route-table module thread-safe.
    
    Due to patch fe83f8 &#40;netdev: Remove netdev from global shash when
    the user is changing interface configuration&#41;, netdevs can be
    destructed and deallocated by revalidator and RCU threads. When
    netdevs with class vport are destroyed, the routing table is
    unregistered, possibly causing memory to be freed. This causes a
    race condition with the main thread which calls route_table_run
    periodically to check for routing table updates.
    
    This patch makes the route-table module thread-safe via a mutex.
    
    Bug #1258532
    Signed-off-by: Ryan Wilson &lt;wryan@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
