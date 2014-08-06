---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6ceb0865-7321-445f-bb57-b3a21d567ebb
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 414da86d-2cbc-4b1a-93f2-63862d1ee0aa
controller          : [6d1a91f8-4db9-40b2-9729-8ef21f12def1]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5b95c793-32a0-4e0f-9c3e-027f2b9503dd, 64b335bf-e3d0-48da-8c1c-3fd10e5643cc, a733cb3e-cbfc-4f3c-ac93-efcdd9dea8d5, fc7f9936-e320-4ce1-9245-15a11daca977]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6d1a91f8-4db9-40b2-9729-8ef21f12def1
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=687, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : fc7f9936-e320-4ce1-9245-15a11daca977
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [db70d0d0-88f9-4b85-8f9c-5640208353a6]
name                : br0

_uuid               : a733cb3e-cbfc-4f3c-ac93-efcdd9dea8d5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6927b011-d21d-4289-bb66-f111e8188421]
name                : eth23

_uuid               : 5b95c793-32a0-4e0f-9c3e-027f2b9503dd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7682a7f2-a9d7-4d97-b105-bc3a2e13b73d]
name                : eth21

_uuid               : 64b335bf-e3d0-48da-8c1c-3fd10e5643cc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a2fb2777-38e7-46d6-b3f0-7072b79ca720]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : db70d0d0-88f9-4b85-8f9c-5640208353a6
admin_state         : down
duplex              : full
ifindex             : 73
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

_uuid               : 6927b011-d21d-4289-bb66-f111e8188421
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2498644500, tx_dropped=0, tx_errors=0, tx_packets=1665763}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 7682a7f2-a9d7-4d97-b105-bc3a2e13b73d
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
statistics          : {collisions=0, rx_bytes=1840259787, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=84290080, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a2fb2777-38e7-46d6-b3f0-7072b79ca720
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1147764172, tx_dropped=0, tx_errors=0, tx_packets=49453306}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fb42720ed20a4268d44df3f39e3ec5fd00261e28
Author:     Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
AuthorDate: Thu Aug 7 01:35:11 2014 +0000
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Wed Aug 6 10:58:22 2014 -0700

    test-atomic: Fix warnings for GCC4.9 and sparse
    
    There's no reason for the local variable 'old_count' to be atomic. In fact, if
    it is atomic it triggers a GCC4.9 warning &#40;Wunused-value&#41;
    The global variables 'a' and 'paux' could be static, according to sparse.
    
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
