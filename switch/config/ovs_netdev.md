---
layout: default
title: ovs_netdev - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
06f35bb5-dd61-4004-8610-ac550f0c4fe3
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth8"
            Interface "eth8"
        Port "eth7"
            Interface "eth7"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge
_uuid               : 3fa7f798-71ae-4c3b-93eb-6e78a79ab99b
controller          : [e2b5a3b2-664d-4026-8181-d01b58e4d42c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0a35a96b-b5c7-4728-be32-57d7b49cd49f, abced7fb-edf9-40c9-91a3-d3ff0ffa5954, fdcbf304-cde7-4285-afe2-b3d4a27b37a0]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : e2b5a3b2-664d-4026-8181-d01b58e4d42c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="301", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : fdcbf304-cde7-4285-afe2-b3d4a27b37a0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7b30e4f5-f13d-4a19-a0a2-7ec8411e14eb]
name                : "br0"

_uuid               : abced7fb-edf9-40c9-91a3-d3ff0ffa5954
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [17d3f430-5090-4a53-95ea-7469e8047fa7]
name                : "eth7"

_uuid               : 0a35a96b-b5c7-4728-be32-57d7b49cd49f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [840dd21f-dcd0-41f7-833d-2b1108375e77]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : 17d3f430-5090-4a53-95ea-7469e8047fa7
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
statistics          : {collisions=0, rx_bytes=1224356, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=12502, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 7b30e4f5-f13d-4a19-a0a2-7ec8411e14eb
admin_state         : up
duplex              : full
ifindex             : 75
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

_uuid               : 840dd21f-dcd0-41f7-833d-2b1108375e77
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=441876, tx_dropped=0, tx_errors=0, tx_packets=4774}
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
