---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ade4a68a-2e89-47d8-9de5-e8a3b8971917
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c12cc007-77ec-46c9-92e1-1fb05250ab10
controller          : [39134967-4a54-40a7-85b0-a3258ebccf50]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1c7ad96c-5892-43df-adea-77e163bf714e, c3d51c32-6e8f-4629-97fc-0260f6427ace, c7ce3d95-cdef-4331-a9a7-3047fa2afc5b, c8e4cb8a-c451-4733-b30a-7c844cbbb9b5]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 39134967-4a54-40a7-85b0-a3258ebccf50
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=1012, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1c7ad96c-5892-43df-adea-77e163bf714e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a5b3cb38-7106-4cc4-a649-e443ecb729bb]
name                : eth21

_uuid               : c7ce3d95-cdef-4331-a9a7-3047fa2afc5b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9857a4f2-5394-4f47-b775-cfe41df79554]
name                : br0

_uuid               : c3d51c32-6e8f-4629-97fc-0260f6427ace
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a3d38c39-95a6-4c9e-a499-18ce93b6e37b]
name                : eth23

_uuid               : c8e4cb8a-c451-4733-b30a-7c844cbbb9b5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [37ef3628-5fa0-4847-87c0-295c6530805a]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a5b3cb38-7106-4cc4-a649-e443ecb729bb
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
statistics          : {collisions=0, rx_bytes=697630273, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=6231673, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 37ef3628-5fa0-4847-87c0-295c6530805a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3667247660, tx_dropped=0, tx_errors=0, tx_packets=2458927}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a3d38c39-95a6-4c9e-a499-18ce93b6e37b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2664117704, tx_dropped=0, tx_errors=0, tx_packets=4639390}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9857a4f2-5394-4f47-b775-cfe41df79554
admin_state         : down
duplex              : full
ifindex             : 300
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 60032110f13552588f68443b646b869369a3f414
Author:     Ryan Wilson &lt;wryan@nicira.com&gt;
AuthorDate: Thu May 29 23:44:37 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Thu May 29 23:48:41 2014 -0700

    ovsdb-idl: Add coverage counters for ovsdb commit return statuses.
    
    Signed-off-by: Ryan Wilson &lt;wryan@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
