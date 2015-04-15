---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
acbb799d-d520-4806-8ffe-f3d005f5a94f
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
_uuid               : d57cdafc-c631-46f9-b8b1-04bb50ecc1ba
controller          : [31197908-d538-4de1-a823-5c532791fcab]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [12e33428-9785-48b6-b067-323e29bb4e4a, 5ee29f40-b469-4101-8390-cfd3a57b0bff, 78073305-b0aa-4394-b9a1-a3ff4c949736, dc90d78a-14ad-4e2d-aa04-9663b54abf03]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 31197908-d538-4de1-a823-5c532791fcab
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="661", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5ee29f40-b469-4101-8390-cfd3a57b0bff
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e01d20d1-3f23-4b36-88e8-5b78e1ac8526]
name                : "eth21"

_uuid               : 12e33428-9785-48b6-b067-323e29bb4e4a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e700479f-d6e1-4912-aa74-79bf4811451a]
name                : "eth23"

_uuid               : 78073305-b0aa-4394-b9a1-a3ff4c949736
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a14b22a1-ca5c-4139-a951-1459119d79ac]
name                : "br0"

_uuid               : dc90d78a-14ad-4e2d-aa04-9663b54abf03
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9eb98172-acd2-43a4-92a5-3c126c1e774a]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e01d20d1-3f23-4b36-88e8-5b78e1ac8526
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
statistics          : {collisions=0, rx_bytes=1231608568336, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=821444688, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a14b22a1-ca5c-4139-a951-1459119d79ac
admin_state         : down
duplex              : full
ifindex             : 895
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

_uuid               : 9eb98172-acd2-43a4-92a5-3c126c1e774a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=630154108798, tx_dropped=0, tx_errors=0, tx_packets=420266584}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : e700479f-d6e1-4912-aa74-79bf4811451a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=40932016500, tx_dropped=0, tx_errors=0, tx_packets=27288011}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ea4226359f634885ed4ff9b9fd291c0b3be93b11
Author:     Kevin Lo &lt;kevlo@FreeBSD.org&gt;
AuthorDate: Wed Apr 15 14:58:39 2015 +0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Apr 15 07:40:33 2015 -0700

    netdev-bsd: Remove duplicate header inclusion of &lt;netinet/in.h&gt;
    
    Signed-off-by: Kevin Lo &lt;kevlo@FreeBSD.org&gt;
    Acked-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
