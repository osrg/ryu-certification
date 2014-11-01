---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d45b0223-7ac5-4acd-bdf0-2341fc5b1161
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
_uuid               : a14a2ceb-f563-4f4c-88c2-c972cf99177c
controller          : [0d89cd2a-62c7-4be1-b114-8109a2580517]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [41e8a600-8773-48d4-adf4-73b63a8bb61a, b0011c8d-1e83-4893-ae7f-03f18e25a1df, c38d1b6a-ba12-4fea-80df-7782762213cb, f107297c-2540-4272-a9ed-77607ffda5ed]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0d89cd2a-62c7-4be1-b114-8109a2580517
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=677, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 41e8a600-8773-48d4-adf4-73b63a8bb61a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b7d0a9af-ac36-45c7-a0d4-97ba3b62a66d]
name                : eth22

_uuid               : f107297c-2540-4272-a9ed-77607ffda5ed
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8ac23012-2cc7-4e13-9036-cae49dca356d]
name                : eth21

_uuid               : b0011c8d-1e83-4893-ae7f-03f18e25a1df
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [84072d0b-ebd4-4473-b59f-d05835d0aad8]
name                : br0

_uuid               : c38d1b6a-ba12-4fea-80df-7782762213cb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [64dd0677-6e1d-4064-bda5-cbaa9692d722]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8ac23012-2cc7-4e13-9036-cae49dca356d
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
statistics          : {collisions=0, rx_bytes=257968564553, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=172085240, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 64dd0677-6e1d-4064-bda5-cbaa9692d722
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=13857996000, tx_dropped=0, tx_errors=0, tx_packets=9238664}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b7d0a9af-ac36-45c7-a0d4-97ba3b62a66d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=158157619512, tx_dropped=0, tx_errors=0, tx_packets=105486437}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 84072d0b-ebd4-4473-b59f-d05835d0aad8
admin_state         : down
duplex              : full
ifindex             : 313
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
commit 712b4d2470ed2e8cfe6bb16080d7e9d54003061a
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Fri Oct 31 14:14:56 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Fri Oct 31 16:28:58 2014 -0700

    test-classifier: Ensure priority is not INT_MIN.
    
    Classifier reserves the priority value INT_MIN for its own use.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
