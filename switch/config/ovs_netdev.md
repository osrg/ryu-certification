---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
486feb08-9dd4-4e40-8c38-1e579e2cf862
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 457d208c-019e-44dc-b7d6-56666845b246
controller          : [8ccf8e3d-3a28-4f2e-a915-b5697bb52b18]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [39a04010-f7ef-4542-b68c-7b704c4f80f0, 99eec857-f5c3-4033-a31e-3861a6f90a72, b9963510-5fce-4aaf-b8b5-c64419b9be4a, c0176820-75fd-4235-973f-7676736f452e]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8ccf8e3d-3a28-4f2e-a915-b5697bb52b18
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=562, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 39a04010-f7ef-4542-b68c-7b704c4f80f0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [11416f3c-02ca-40b8-84ec-aa298e2a7db5]
name                : eth22

_uuid               : c0176820-75fd-4235-973f-7676736f452e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a44e0d43-4825-46ef-ab84-685a5a3e6d86]
name                : eth21

_uuid               : b9963510-5fce-4aaf-b8b5-c64419b9be4a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8838e3fb-81dc-423d-b470-a93a08488b72]
name                : eth23

_uuid               : 99eec857-f5c3-4033-a31e-3861a6f90a72
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b31fc3ad-3b3c-414e-b68f-e42b237ec410]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 11416f3c-02ca-40b8-84ec-aa298e2a7db5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=385013052, tx_dropped=0, tx_errors=0, tx_packets=258038}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b31fc3ad-3b3c-414e-b68f-e42b237ec410
admin_state         : down
duplex              : full
ifindex             : 63
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

_uuid               : 8838e3fb-81dc-423d-b470-a93a08488b72
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=877246500, tx_dropped=0, tx_errors=0, tx_packets=584831}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a44e0d43-4825-46ef-ab84-685a5a3e6d86
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
statistics          : {collisions=0, rx_bytes=1122112896, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=751835, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9421a1f69a1f3b069a3b38fdb580a5aeb0c348ce
Author:     Ryan Wilson &lt;wryan@nicira.com&gt;
AuthorDate: Mon May 19 00:09:24 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon May 19 08:19:20 2014 -0700

    ovs-rcu: Add OVSRCU_TYPE_INITIALIZER which initializes OVSRCU_TYPE variables to NULL.
    
    Signed-off-by: Ryan Wilson &lt;wryan@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
