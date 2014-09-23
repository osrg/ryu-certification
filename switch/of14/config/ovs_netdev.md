---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a6b4938f-36bc-4323-82de-614fb0aa0fbc
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
_uuid               : 0a9175fa-0bbd-4536-915d-6150edd2e67b
controller          : [f5cfacc8-1d2a-4f03-a05a-877d3fd134c9]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [37138c33-e3dc-4bbd-873f-84803b013e94, af106bf0-ff5d-4d3b-a8d2-bc15178af7bd, b0082e7a-604f-459c-b88f-62d8cf6dcea7, dcba3ae2-7df6-470e-9bd5-19814eacb5bf]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f5cfacc8-1d2a-4f03-a05a-877d3fd134c9
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=666, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : af106bf0-ff5d-4d3b-a8d2-bc15178af7bd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [eac93bb4-3cd4-4b6b-a67c-e91f9364c2ca]
name                : eth21

_uuid               : b0082e7a-604f-459c-b88f-62d8cf6dcea7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e5132d6d-e2b8-4099-878d-3fee237db8fa]
name                : eth22

_uuid               : dcba3ae2-7df6-470e-9bd5-19814eacb5bf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b10ad253-0423-4cf9-834b-fe2a9a565326]
name                : br0

_uuid               : 37138c33-e3dc-4bbd-873f-84803b013e94
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b6004e22-e6e9-4311-9021-d59ccd5bb8a3]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : eac93bb4-3cd4-4b6b-a67c-e91f9364c2ca
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
statistics          : {collisions=0, rx_bytes=397393265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=74762852, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e5132d6d-e2b8-4099-878d-3fee237db8fa
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2339485610, tx_dropped=0, tx_errors=0, tx_packets=47396053}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b6004e22-e6e9-4311-9021-d59ccd5bb8a3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2638871204, tx_dropped=0, tx_errors=0, tx_packets=4622559}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b10ad253-0423-4cf9-834b-fe2a9a565326
admin_state         : down
duplex              : full
ifindex             : 168
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
