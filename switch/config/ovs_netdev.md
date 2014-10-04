---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
94cc19b8-4ed3-4d5e-bdbd-fcb5b6e707bd
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
_uuid               : 369ef6b3-b8bb-460b-893a-fa775302f61a
controller          : [54c85710-3d36-4dfe-a89b-774eb64d5eb0]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2d11a472-3a37-4ae1-af7e-c2194e3ca068, 65b5b77e-b9fe-4a56-95e2-f06854cfa5e0, 816db61d-ed34-4472-831a-e3e3be2064b8, 9df31fe8-81a1-47b1-8d21-e4bbd0735b9e]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 54c85710-3d36-4dfe-a89b-774eb64d5eb0
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=672, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9df31fe8-81a1-47b1-8d21-e4bbd0735b9e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7e9e953d-1ac6-400f-8a0b-de4ac1964429]
name                : eth23

_uuid               : 816db61d-ed34-4472-831a-e3e3be2064b8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f5ef335a-5831-4a95-80f5-de40ec11a112]
name                : br0

_uuid               : 65b5b77e-b9fe-4a56-95e2-f06854cfa5e0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5d7bbaff-71e4-4815-866a-7870d9dcf8d4]
name                : eth21

_uuid               : 2d11a472-3a37-4ae1-af7e-c2194e3ca068
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ba6dc16a-7040-4a97-86c8-b11490431a61]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7e9e953d-1ac6-400f-8a0b-de4ac1964429
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=225371908, tx_dropped=0, tx_errors=0, tx_packets=5876871}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ba6dc16a-7040-4a97-86c8-b11490431a61
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=592107188, tx_dropped=0, tx_errors=0, tx_packets=60554486}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f5ef335a-5831-4a95-80f5-de40ec11a112
admin_state         : down
duplex              : full
ifindex             : 207
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

_uuid               : 5d7bbaff-71e4-4815-866a-7870d9dcf8d4
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
statistics          : {collisions=0, rx_bytes=3343423613, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=99648400, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 705e9260d54d55ed1d484a8fead27f33f714a94c
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Mon Sep 29 21:39:56 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Fri Oct 3 15:38:53 2014 -0700

    datapath: Add support for RHEL-7 / CentOS-7 kernel.
    
    This patch mostly is related to tunnel API where RHEL 7
    kernel API are not in-sync with newer linux kernel API. So
    extra checks are required to check for parameters of API.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Jiri Benc &lt;jbenc@redhat.com&gt;
</pre>
