---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f9975718-6f11-4b2f-ae50-244d1aecd500
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 1543f149-9625-47ec-86ec-060df1f13092
controller          : [9b8aa39e-5a40-4223-869a-2a521830abbd]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [22f0e160-8439-4e58-9ae5-1dbf1a06530b, 2e80b182-099a-4dd8-a9d7-b4f47abf4d5e, 3575b65a-75bf-49e6-806d-440513122cec, dfd27a48-e794-489a-8713-54c0e3c98c6b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9b8aa39e-5a40-4223-869a-2a521830abbd
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=1417, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 22f0e160-8439-4e58-9ae5-1dbf1a06530b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8b735ccd-b8a3-4266-bd90-7bd7e427f458]
name                : eth22

_uuid               : dfd27a48-e794-489a-8713-54c0e3c98c6b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f3973732-2484-4631-967c-a03565fc8919]
name                : br0

_uuid               : 3575b65a-75bf-49e6-806d-440513122cec
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7be223f0-fac8-4bfb-be03-0f8ab919298d]
name                : eth23

_uuid               : 2e80b182-099a-4dd8-a9d7-b4f47abf4d5e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e95d0ae7-41cc-4425-9e86-ae5f6c2bbfd8]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7be223f0-fac8-4bfb-be03-0f8ab919298d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=277720408, tx_dropped=0, tx_errors=0, tx_packets=5911770}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8b735ccd-b8a3-4266-bd90-7bd7e427f458
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3719082812, tx_dropped=0, tx_errors=0, tx_packets=11089727}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f3973732-2484-4631-967c-a03565fc8919
admin_state         : down
ifindex             : 384
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : e95d0ae7-41cc-4425-9e86-ae5f6c2bbfd8
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
statistics          : {collisions=0, rx_bytes=881253576, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=23550174, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit b250cce49faa7383fd445c8f0d9e7d12b321e69c
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Thu Jun 5 09:48:25 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Thu Jun 5 09:48:25 2014 -0700

    tests/ofproto-dpif.at: Add delay before stopping time.
    
    Add 2 second sleep before time stop to allow internal ports to
    reconnect in case the initial connection attempt failed.
    
    Bond tests sometimes persistently fail without these delays.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
