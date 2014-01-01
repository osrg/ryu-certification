---
layout: default
title: ovs - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f5d928a7-8630-44db-a563-1862bd699a12
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth8"
            Interface "eth8"
        Port "eth7"
            Interface "eth7"

$ sudo ovs-vsctl list Bridge
_uuid               : 5f363cfb-d1e4-4983-949c-a1f65743193a
controller          : [d3dd8a45-2a5f-43f9-b2a5-618242c33c5c]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3e82d661-f894-4a75-bfb6-06acec121835, 7b733c21-52ad-4241-9d0e-79d56515c24a, 933fe341-391b-4197-9283-c9ffd0ec707b]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : d3dd8a45-2a5f-43f9-b2a5-618242c33c5c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="352", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 3e82d661-f894-4a75-bfb6-06acec121835
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2bc0b13c-1f5d-492a-8e5a-3b4a2a29f1c7]
name                : "br0"

_uuid               : 7b733c21-52ad-4241-9d0e-79d56515c24a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [726c2154-fdcb-42fa-9ddd-0bd976f6003b]
name                : "eth8"

_uuid               : 933fe341-391b-4197-9283-c9ffd0ec707b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [84adca1a-92cb-4128-8485-911030924ae2]
name                : "eth7"

$ sudo ovs-vsctl list Interface
_uuid               : 726c2154-fdcb-42fa-9ddd-0bd976f6003b
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:ec"
mtu                 : 1550
name                : "eth8"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 2bc0b13c-1f5d-492a-8e5a-3b4a2a29f1c7
admin_state         : up
ifindex             : 77
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 84adca1a-92cb-4128-8485-911030924ae2
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "eth7"
ofport              : 1
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 21e70add7e5fc18c519ca3d46691230bf136b1e1
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Dec 31 10:36:19 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Dec 31 11:42:52 2013 -0800

    odp-util: Simplify logic in odp_flow_key_to_flow__().
    
    Simplify (a &amp;&amp; b) || (!a &amp;&amp; c) to just a ? b : c.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
