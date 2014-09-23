---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
32a7894c-21c3-42b6-bdbf-06d9381bfd64
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : bb851fa3-db4e-412b-ade8-5476d192d426
controller          : [9a7d9c8f-c6fd-4b9d-977a-8661363e2612]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [be357cf3-8003-499e-8ff8-29efb91991e6, c45adcb0-2da1-4db3-bc0b-f7bbeb38770e, d7a10f6f-0682-4f2d-a5bd-d093e5eab66b, e90fe046-3e8a-4bbb-8c43-4249b2baf44c]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9a7d9c8f-c6fd-4b9d-977a-8661363e2612
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=682, sec_since_disconnect=6, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c45adcb0-2da1-4db3-bc0b-f7bbeb38770e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2d13a127-8ed5-4e89-8d8c-7214561cb79b]
name                : eth23

_uuid               : e90fe046-3e8a-4bbb-8c43-4249b2baf44c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9bbeb08b-7cf2-4473-b926-4d769e954924]
name                : eth21

_uuid               : d7a10f6f-0682-4f2d-a5bd-d093e5eab66b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [beadc0c1-6d33-4228-bc93-b32216eff986]
name                : eth22

_uuid               : be357cf3-8003-499e-8ff8-29efb91991e6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f8381cf8-673b-4a71-81f1-50c340a9c167]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f8381cf8-673b-4a71-81f1-50c340a9c167
admin_state         : down
duplex              : full
ifindex             : 166
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

_uuid               : beadc0c1-6d33-4228-bc93-b32216eff986
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2287043950, tx_dropped=0, tx_errors=0, tx_packets=47360799}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2d13a127-8ed5-4e89-8d8c-7214561cb79b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2551079204, tx_dropped=0, tx_errors=0, tx_packets=4564031}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9bbeb08b-7cf2-4473-b926-4d769e954924
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
statistics          : {collisions=0, rx_bytes=280522557, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=74684307, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 4a1f9610682d785e18fd38f86d81a66aa212789f
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Mon Sep 22 15:34:12 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Mon Sep 22 18:38:25 2014 -0700

    ovs-pki: Use SHA-1 instead of SHA-512 as message digest.
    
    Commit 9ff33ca7 &#40;ovs-pki: Use SHA-512 instead of MD5 as message
    digest.&#41; changes the message digest algorithm to SHA-512.  This
    seems to break the unit tests on some xenserver 5.6/6.0 builds
    causing the error: &quot;SSL_connect: error:0D0C50A1:asn1 encoding
    routines:ASN1_item_verify:unknown message digest algorithm&quot;.
    
    As a solution, this commit changes the message digest algorithm
    to SHA-1 which works for both the above xenserver builds and
    centos 7.
    
    VMware-BZ: #1319116
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
