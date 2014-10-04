---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
09bfcbcd-0eea-42bb-8c65-0a00f4a7863b
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
_uuid               : 0fdaca53-464e-4b49-985d-034649cc6aee
controller          : [3bf5fb32-5b2e-4a8c-a063-0d46da58a0d4]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [07cb3c6f-f14b-4cb6-b4de-473d563d1da7, c47d9466-f62e-4fd6-82d5-cd4206acd4cb, c983bdc4-03ea-49bf-9eee-d782ccd4c120, fd36ea57-e6e4-4e24-a2ed-fd4bd76eb09d]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3bf5fb32-5b2e-4a8c-a063-0d46da58a0d4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=667, sec_since_disconnect=6, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c983bdc4-03ea-49bf-9eee-d782ccd4c120
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b81345c5-988b-48c2-9b81-9a45242af0cd]
name                : eth22

_uuid               : c47d9466-f62e-4fd6-82d5-cd4206acd4cb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fd49f069-fe6d-4429-9c2f-efaa8b1b4dd2]
name                : eth23

_uuid               : 07cb3c6f-f14b-4cb6-b4de-473d563d1da7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fb243cef-de3a-4850-b3f2-ca3ade58bfc4]
name                : br0

_uuid               : fd36ea57-e6e4-4e24-a2ed-fd4bd76eb09d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bdfc0729-9234-4fde-98b3-b722b9f806c5]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b81345c5-988b-48c2-9b81-9a45242af0cd
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=644574348, tx_dropped=0, tx_errors=0, tx_packets=60589757}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : bdfc0729-9234-4fde-98b3-b722b9f806c5
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
statistics          : {collisions=0, rx_bytes=3460309321, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=99726955, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : fd49f069-fe6d-4429-9c2f-efaa8b1b4dd2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=313153408, tx_dropped=0, tx_errors=0, tx_packets=5935392}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : fb243cef-de3a-4850-b3f2-ca3ade58bfc4
admin_state         : down
duplex              : full
ifindex             : 209
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
