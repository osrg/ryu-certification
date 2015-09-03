---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d7aec9fd-62bc-4520-a69c-cc0cb03b1d21
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : fcdb4ffe-770a-441b-a157-06ec74fad118
controller          : [a812f728-a0e3-4f06-b639-6de9e006c289]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [64320692-7896-4a35-90e4-fc123e849193, 88198c72-2aba-4514-8718-a181d80ea625, daa133c6-893b-419d-8062-e95e644de852, f75ff3ad-e526-4750-b1bf-a3c85f38fb91]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a812f728-a0e3-4f06-b639-6de9e006c289
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f75ff3ad-e526-4750-b1bf-a3c85f38fb91
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d13c7c32-e3b1-49c5-8ba2-4bf596d2b41c]
name                : "eth22"

_uuid               : daa133c6-893b-419d-8062-e95e644de852
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [76447894-551b-4fd0-a188-121ac14af008]
name                : "br0"

_uuid               : 64320692-7896-4a35-90e4-fc123e849193
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aa00248a-a191-492f-abaa-5686e40ba6e9]
name                : "eth23"

_uuid               : 88198c72-2aba-4514-8718-a181d80ea625
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6d46f5f5-01c6-4f3b-a7ee-8d36f0be5da9]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 76447894-551b-4fd0-a188-121ac14af008
admin_state         : down
duplex              : full
ifindex             : 421
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : 6d46f5f5-01c6-4f3b-a7ee-8d36f0be5da9
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=24024581534, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16026376, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d13c7c32-e3b1-49c5-8ba2-4bf596d2b41c
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18089315792, tx_dropped=0, tx_errors=0, tx_packets=12064077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : aa00248a-a191-492f-abaa-5686e40ba6e9
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1176922500, tx_dropped=0, tx_errors=0, tx_packets=784615}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 554daf066bf4a8eb7bbc8edc1a877a3afc0de38d
Author:     Jason Kölker &lt;jason@koelker.net&gt;
AuthorDate: Wed Sep 2 22:40:24 2015 +0000
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Wed Sep 2 15:46:50 2015 -0700

    datapath: Add net/ip6_checksum.h to stt.c
    
    `csum_ipv6_magic` is an asm inline on most platforms. However if it is
    not defined &#40;like on ppc64le&#41; including &lt;net/ip6_checksum.h&gt; will fall
    back to the c implementation by wrapping it in an
    `#ifndef _HAVE_ARCH_IPV6_CSUM`.
    
    Signed-off-by: Jason Kölker &lt;jason@koelker.net&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
