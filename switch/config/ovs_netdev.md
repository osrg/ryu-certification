---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d3f9654b-91ad-437a-9918-f9292be66f54
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 782454ec-eaad-4e4c-8c20-8a8d0a45ccce
controller          : [fa48c359-7323-4e1b-b2cd-79012a8c725f]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [74cc471b-ba8e-4c4f-ba3e-4412221049ef, b1b24a61-933d-4888-9796-c565d4cfbe3a, edaf4f7e-352a-4630-90ac-b04d2d1c52ca, ffd55ad3-627f-4603-94ca-53d7ecb0066a]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : fa48c359-7323-4e1b-b2cd-79012a8c725f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=972, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b1b24a61-933d-4888-9796-c565d4cfbe3a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e9671871-4614-4e68-af98-0ff55ffb595d]
name                : eth23

_uuid               : edaf4f7e-352a-4630-90ac-b04d2d1c52ca
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [be84c061-4291-4708-9a68-135dd6b1fcba]
name                : eth21

_uuid               : 74cc471b-ba8e-4c4f-ba3e-4412221049ef
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [94a83c42-04d4-4c97-aae5-7c361f5752af]
name                : br0

_uuid               : ffd55ad3-627f-4603-94ca-53d7ecb0066a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a68597ea-702c-4f11-8d74-a191e9aa5aaa]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e9671871-4614-4e68-af98-0ff55ffb595d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3896561204, tx_dropped=0, tx_errors=0, tx_packets=5461019}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : be84c061-4291-4708-9a68-135dd6b1fcba
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
statistics          : {collisions=0, rx_bytes=3515935718, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=10982576, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 94a83c42-04d4-4c97-aae5-7c361f5752af
admin_state         : down
duplex              : full
ifindex             : 356
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

_uuid               : a68597ea-702c-4f11-8d74-a191e9aa5aaa
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2762311124, tx_dropped=0, tx_errors=0, tx_packets=4722206}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 29d204effc1b5301c0312b45744d1730706024a5
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Wed Jun 4 09:15:48 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Wed Jun 4 09:20:46 2014 -0700

    INSTALL: Note about compiler atomics support.
    
    OVS is slow when compiled with pthreads atomics.  Add a generic note
    in INSTALL, with a reference to lib/ovs-atomic.h, where a new comment
    provides additional detail.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
