---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
13294b69-8b97-45d5-9530-2c48d64073cb
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 39941e83-0e75-42d5-8d91-45ea6e91b90f
controller          : [dcdaaadd-e1c6-41b5-8320-72f472619710]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [25cf90b7-e112-4bcf-9acf-17fa5463b2c8, 2bb064fd-7cef-4487-81b1-e488b6690504, e1ef9b7d-1d16-433d-89b7-86d4286cbc5e, f79603e1-c539-476e-99e5-f62697687fdc]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : dcdaaadd-e1c6-41b5-8320-72f472619710
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="747", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f79603e1-c539-476e-99e5-f62697687fdc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [038a7784-c48c-40a6-8db5-26d614bcd37a]
name                : "eth23"

_uuid               : 2bb064fd-7cef-4487-81b1-e488b6690504
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0a8d7881-7dc6-469c-b79a-eb3d2f2b3470]
name                : "br0"

_uuid               : e1ef9b7d-1d16-433d-89b7-86d4286cbc5e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2218e7d9-5089-48a1-902e-bfe34f07d8b6]
name                : "eth21"

_uuid               : 25cf90b7-e112-4bcf-9acf-17fa5463b2c8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f2806166-8bdb-4d03-801f-a759c1a61b82]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 038a7784-c48c-40a6-8db5-26d614bcd37a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2128278000, tx_dropped=0, tx_errors=0, tx_packets=1418852}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 0a8d7881-7dc6-469c-b79a-eb3d2f2b3470
admin_state         : down
duplex              : full
ifindex             : 545
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

_uuid               : 2218e7d9-5089-48a1-902e-bfe34f07d8b6
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
statistics          : {collisions=0, rx_bytes=36556747579, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=24388754, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f2806166-8bdb-4d03-801f-a759c1a61b82
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=26613030238, tx_dropped=0, tx_errors=0, tx_packets=17749968}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3ca600a3e1b2cc67128ff3cbda42e5adc0376e5c
Author:     Gurucharan Shetty &lt;shettyg@nicira.com&gt;
AuthorDate: Wed Sep 30 14:18:47 2015 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Thu Oct 8 08:41:47 2015 -0700

    poll-loop: Fix a bug while finding a poll node.
    
    When a poll_node is created, it gets either a 'fd' or
    a 'wevent' &#40;can't get both&#41;. When the poll_node is
    searched for previous creations on that 'fd' or 'wevent',
    the search criteria was wrong for Windows. In Windows,
    when a 'fd' is received in poll_create_node, we create a
    corresponding 'wevent'. So while searching for that 'fd',
    we should not look for 'wevent' in the hmap_node.
    
    Reported-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
