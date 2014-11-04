---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
99be2967-a4c5-41e6-96e6-6537aae70680
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 2888e167-ca0c-4e67-b965-6b1ae905ed61
controller          : [fa1e1261-0368-4a80-b06a-42ae8da9e73a]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [042d747f-7b93-41bc-8a0d-a4f28d0e9ca4, 788c0468-8f1d-42a1-ab2d-098f9ad5dcb6, d68489f5-edeb-4792-882b-dfe748dc5677, f4ee018b-b92e-4c9d-b22b-e65e390bbf0d]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : fa1e1261-0368-4a80-b06a-42ae8da9e73a
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=847, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 788c0468-8f1d-42a1-ab2d-098f9ad5dcb6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aaac68da-9003-4b17-9bba-6ecd4d43520a]
name                : eth21

_uuid               : d68489f5-edeb-4792-882b-dfe748dc5677
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [10269536-970a-430f-bf1c-599e51982521]
name                : eth22

_uuid               : 042d747f-7b93-41bc-8a0d-a4f28d0e9ca4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [58f56f72-3205-491b-b12d-9b2775336ee1]
name                : eth23

_uuid               : f4ee018b-b92e-4c9d-b22b-e65e390bbf0d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [50570446-fbdc-43ef-b07b-c4deaea9a88e]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : aaac68da-9003-4b17-9bba-6ecd4d43520a
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
statistics          : {collisions=0, rx_bytes=270882796311, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=180698433, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 58f56f72-3205-491b-b12d-9b2775336ee1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=14231044500, tx_dropped=0, tx_errors=0, tx_packets=9487363}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 10269536-970a-430f-bf1c-599e51982521
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=160610258110, tx_dropped=0, tx_errors=0, tx_packets=107123059}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 50570446-fbdc-43ef-b07b-c4deaea9a88e
admin_state         : down
duplex              : full
ifindex             : 320
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
commit 495a6c342b3fc38c375b20cd2dcd9b9ac9017b64
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Tue Nov 4 09:24:24 2014 -0800
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Tue Nov 4 09:48:17 2014 -0800

    ovs-router: Fix sparse warning
    
    Fixes following warning:
    ../lib/ovs-router.c:162:11: warning: incorrect type in assignment
    &#40;different base types&#41;
    ../lib/ovs-router.c:162:11:    expected restricted ovs_be32
    [usertype] &lt;noident&gt;
    ../lib/ovs-router.c:162:11:    got restricted ovs_be16
    
    Reported-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
