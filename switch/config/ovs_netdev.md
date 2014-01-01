---
layout: default
title: ovs_netdev - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
629342c1-4ec3-424a-926c-77bca48a2aa6
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
_uuid               : 3c21a38d-76e1-4501-9511-e2ad1239ce85
controller          : [397a613f-d262-4861-8ad8-08afdc897420]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [4937d2f4-26b9-42d9-8227-4bc6545a818d, d60f9fd0-a697-437a-9d07-cf31ecc00840, e35cfe9c-15d8-4909-9ec3-13e564872975]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 397a613f-d262-4861-8ad8-08afdc897420
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="296", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : e35cfe9c-15d8-4909-9ec3-13e564872975
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8d9e318c-aa17-4c1f-b138-835c0f515895]
name                : "br0"

_uuid               : 4937d2f4-26b9-42d9-8227-4bc6545a818d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [65981577-3218-4c4f-bc41-7665dccfefd8]
name                : "eth7"

_uuid               : d60f9fd0-a697-437a-9d07-cf31ecc00840
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dd5ea2d4-135d-4012-a0ae-6817caeb8dde]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : dd5ea2d4-135d-4012-a0ae-6817caeb8dde
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=421568, tx_dropped=0, tx_errors=0, tx_packets=4554}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 8d9e318c-aa17-4c1f-b138-835c0f515895
admin_state         : up
duplex              : full
ifindex             : 73
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : 65981577-3218-4c4f-bc41-7665dccfefd8
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
statistics          : {collisions=0, rx_bytes=1159091, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=11842, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 21e70add7e5fc18c519ca3d46691230bf136b1e1
Author:     Ben Pfaff &amp;lt;blp@nicira.com&amp;gt;
AuthorDate: Tue Dec 31 10:36:19 2013 -0800
Commit:     Ben Pfaff &amp;lt;blp@nicira.com&amp;gt;
CommitDate: Tue Dec 31 11:42:52 2013 -0800

    odp-util: Simplify logic in odp_flow_key_to_flow__().
    
    Simplify (a &amp;&amp; b) || (!a &amp;&amp; c) to just a ? b : c.
    
    Signed-off-by: Ben Pfaff &amp;lt;blp@nicira.com&amp;gt;
</pre>
