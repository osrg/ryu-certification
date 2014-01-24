---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
494bb648-eceb-44e7-b807-d52d26a58954
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
_uuid               : fe999898-43d7-466a-875b-bdabc6aec042
controller          : [0d28fed8-0efd-4540-8db6-fa162d99c9b4]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [77d1ec3b-3dcd-450e-9a41-755f8b0eb2bf, 8b5981ea-52c7-4c94-ac7c-7b31df2996ce, 973b6cf7-367f-4a2d-ac59-f061ac20377a]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0d28fed8-0efd-4540-8db6-fa162d99c9b4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=302, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8b5981ea-52c7-4c94-ac7c-7b31df2996ce
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e52a74c5-ca33-4503-898e-eb3882177a9a]
name                : eth8

_uuid               : 77d1ec3b-3dcd-450e-9a41-755f8b0eb2bf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [34ba5377-b1d1-4a87-9383-bbba9f61e87a]
name                : eth7

_uuid               : 973b6cf7-367f-4a2d-ac59-f061ac20377a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a585ff0b-a246-4d27-b2f6-6c2e81f8dc55]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e52a74c5-ca33-4503-898e-eb3882177a9a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=152372, tx_dropped=0, tx_errors=0, tx_packets=1623}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 34ba5377-b1d1-4a87-9383-bbba9f61e87a
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
statistics          : {collisions=0, rx_bytes=597925, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=6028, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : a585ff0b-a246-4d27-b2f6-6c2e81f8dc55
admin_state         : up
duplex              : full
ifindex             : 58
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 631486bd29dc6cfe2dc7cf65495d308f4c7fca56
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Wed Dec 18 13:55:25 2013 -0800
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Thu Jan 23 16:08:53 2014 -0800

    netdev-dummy: Add support for active stream
    
    The dummy ports thus far only support passive connections. It can
    listen for multiple incoming connection requests but not make active
    connections. This patch adds support of active stream, so that a
    dummy port can be configured with either passive or active connections.
    
    The net result is that dummy ports can now connect to each other,
    without being patch ports. This feature will be useful in adding test
    cases of future commits.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
