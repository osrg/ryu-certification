---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2e85e62e-9546-4040-ad1d-b93ca48f73f0
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c61770a2-8ee7-46ba-b87c-7751dcd6fdb1
controller          : [a6f3f661-da2e-4041-ab4b-411cc827663d]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2e3e5683-6e11-486c-832a-54eb9978d96d, 93f44c12-6915-4c9b-b250-5506b1e6fba0, a4a90200-8a0f-4b03-8b4c-2726335cd699, e293369d-8c32-4c13-ba0a-526416730ebf]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a6f3f661-da2e-4041-ab4b-411cc827663d
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a4a90200-8a0f-4b03-8b4c-2726335cd699
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [14b30182-ab48-4205-81b9-4d1a2f9a763f]
name                : "eth23"

_uuid               : e293369d-8c32-4c13-ba0a-526416730ebf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e230e2c5-c7c5-499c-8b29-5f64e3cfab1b]
name                : "eth22"

_uuid               : 93f44c12-6915-4c9b-b250-5506b1e6fba0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [760cab4c-8621-49e3-8b33-7def318863af]
name                : "eth21"

_uuid               : 2e3e5683-6e11-486c-832a-54eb9978d96d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9c0d4a20-33bf-4df6-a1c1-6b6b7a8ed4dd]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 760cab4c-8621-49e3-8b33-7def318863af
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

_uuid               : 9c0d4a20-33bf-4df6-a1c1-6b6b7a8ed4dd
admin_state         : down
duplex              : full
ifindex             : 237
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

_uuid               : e230e2c5-c7c5-499c-8b29-5f64e3cfab1b
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

_uuid               : 14b30182-ab48-4205-81b9-4d1a2f9a763f
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
commit 943f394ea332837d8e5285986c5182e9746c6c62
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Tue Jul 7 18:59:13 2015 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Thu Jul 9 12:53:58 2015 -0700

    db-ctl-base: fix a few typos
    
    Minor typo and style fixes.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
