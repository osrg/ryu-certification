---
layout: default
title: ovs - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8c774f82-cec4-442f-94cc-50f7bfcc778e
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth7"
            Interface "eth7"
        Port "eth8"
            Interface "eth8"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge
_uuid               : acea22d6-a042-458b-b366-3ef288d64c92
controller          : [f1302bc5-91e0-4a7f-a4b8-fb512adbef78]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [4cdba301-9dcc-4636-aaa2-5a3cfbb37e79, 84c1c8b9-d7f1-4e52-8a16-41cd90070d73, ca72c1bc-82ca-4e17-ad79-a7929028c9b8]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : f1302bc5-91e0-4a7f-a4b8-fb512adbef78
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="356", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : ca72c1bc-82ca-4e17-ad79-a7929028c9b8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [47ec5eae-ce90-4517-97ce-17471eca2b7c]
name                : "br0"

_uuid               : 84c1c8b9-d7f1-4e52-8a16-41cd90070d73
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1e1ef138-ce61-42c3-bb74-4a0d80dc536f]
name                : "eth8"

_uuid               : 4cdba301-9dcc-4636-aaa2-5a3cfbb37e79
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d8d4aee2-e3b7-4d3e-aa50-d5ed2ef64d22]
name                : "eth7"

$ sudo ovs-vsctl list Interface
_uuid               : 1e1ef138-ce61-42c3-bb74-4a0d80dc536f
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

_uuid               : d8d4aee2-e3b7-4d3e-aa50-d5ed2ef64d22
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

_uuid               : 47ec5eae-ce90-4517-97ce-17471eca2b7c
admin_state         : up
ifindex             : 71
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
    
    Simplify (a && b) || (!a && c) to just a ? b : c.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
