---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
30e109de-2792-47e2-903d-b375d0109201
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c8dc502a-3eb4-42fc-b6cc-9d1ae29306c7
controller          : [74d95a27-3a85-4188-8a7d-1a9037376649]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [8e588b9d-538d-428c-a196-ba819d29bbc8, c87e219b-59d4-4625-8338-7c15fefa5fcd, ced702f0-9255-459c-820c-ebb9939f95e3, fe6ee5fa-3746-49ed-a6ea-92f42fc1cf5c]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 74d95a27-3a85-4188-8a7d-1a9037376649
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ced702f0-9255-459c-820c-ebb9939f95e3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9cfb15c6-11f9-4fc8-9bc5-b2915ae15a92]
name                : "br0"

_uuid               : 8e588b9d-538d-428c-a196-ba819d29bbc8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aece5c42-d7f0-48fa-bacb-6603d77425dc]
name                : "eth23"

_uuid               : fe6ee5fa-3746-49ed-a6ea-92f42fc1cf5c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3f024151-8e00-44dd-81a9-fd4f589c0e85]
name                : "eth21"

_uuid               : c87e219b-59d4-4625-8338-7c15fefa5fcd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [06963146-9429-4331-8e80-2ce23dc55318]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3f024151-8e00-44dd-81a9-fd4f589c0e85
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

_uuid               : 9cfb15c6-11f9-4fc8-9bc5-b2915ae15a92
admin_state         : down
duplex              : full
ifindex             : 351
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

_uuid               : aece5c42-d7f0-48fa-bacb-6603d77425dc
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

_uuid               : 06963146-9429-4331-8e80-2ce23dc55318
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 43b2f131a229238619ed9ae9ee64092fcae092ca
Author:     Ethan Jackson &lt;ethan@nicira.com&gt;
AuthorDate: Mon Aug 3 18:43:53 2015 -0700
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Thu Aug 13 13:06:59 2015 -0700

    ofproto: Allow in-place modifications of datapath flows.
    
    There are certain use cases &#40;such as bond rebalancing&#41; where a
    datapath flow's actions may change, while it's wildcard pattern
    remains the same.  Before this patch, revalidators would note the
    change, delete the flow, and wait for the handlers to install an
    updated version.  This is inefficient, as many packets could get
    punted to userspace before the new flow is finally installed.
    
    To improve the situation, this patch implements in place modification
    of datapath flows.  If the revalidators detect the only change to a
    given ukey is its actions, instead of deleting it, it does a put with
    the MODIFY flag set.
    
    Signed-off-by: Ethan J. Jackson &lt;ethan@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
