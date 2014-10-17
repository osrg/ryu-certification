---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
aeb874f9-395e-4898-9b6a-472996193bd9
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
_uuid               : 745ca752-19f7-4c21-9240-280c07c23ebb
controller          : [510536d1-80eb-4c45-b8be-a39fafb1bdc1]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [481719cf-ac54-429a-8bfa-1ccee2cf87ac, c32c128b-6bba-4310-983d-9f99d73b4059, c65717e9-4c1c-49ad-8fb7-37cffe4edbbf, e7a6c35f-2bdc-4dd3-8778-6df7b1410c0c]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 510536d1-80eb-4c45-b8be-a39fafb1bdc1
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=697, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c65717e9-4c1c-49ad-8fb7-37cffe4edbbf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4517add8-3d3a-4ef7-bfcf-278e044f9edd]
name                : eth21

_uuid               : 481719cf-ac54-429a-8bfa-1ccee2cf87ac
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [07a0b085-ec18-4cac-8f65-930fc479cba1]
name                : eth23

_uuid               : c32c128b-6bba-4310-983d-9f99d73b4059
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [683eb1dc-6042-4d79-a482-9fdfc1f4ddb6]
name                : br0

_uuid               : e7a6c35f-2bdc-4dd3-8778-6df7b1410c0c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7fcd303c-b584-44d3-b911-6f2e40d1bb6a]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 683eb1dc-6042-4d79-a482-9fdfc1f4ddb6
admin_state         : down
duplex              : full
ifindex             : 258
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

_uuid               : 4517add8-3d3a-4ef7-bfcf-278e044f9edd
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
statistics          : {collisions=0, rx_bytes=1210813217, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=169831149, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 7fcd303c-b584-44d3-b911-6f2e40d1bb6a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1982699290, tx_dropped=0, tx_errors=0, tx_packets=104440827}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 07a0b085-ec18-4cac-8f65-930fc479cba1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2798924908, tx_dropped=0, tx_errors=0, tx_packets=7592573}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit cfa57405bb7f22ad587b33a030bf1e8c10fbda8d
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Thu Oct 16 17:49:01 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Fri Oct 17 10:09:22 2014 -0700

    xenserver: Add ovs-docker to the spec file.
    
    Fixes a rpmbuild failure.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
