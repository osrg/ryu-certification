---
layout: default
title: ovs_netdev - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
99aeda39-7cbe-460c-bca8-166a657523d8
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth7"
            Interface "eth7"
        Port "eth8"
            Interface "eth8"

$ sudo ovs-vsctl list Bridge
_uuid               : 2e8ae4d2-a889-4a89-94d2-088fdde779d6
controller          : [535ea347-0dfb-48c7-b999-f6dec8ebac32]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2b30c598-e7af-4d3f-a26e-a003e53166b4, ca07cf88-fb27-4bd2-9d41-ac5ffb1c3404, d3bf94c7-dc37-47ff-b5f2-3ca0fb506f78]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 535ea347-0dfb-48c7-b999-f6dec8ebac32
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="297", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : ca07cf88-fb27-4bd2-9d41-ac5ffb1c3404
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5bef7f0e-ea58-42b4-b0bf-bbe834433858]
name                : "eth7"

_uuid               : 2b30c598-e7af-4d3f-a26e-a003e53166b4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4f7628df-16f6-479b-8385-94bd509370f3]
name                : "br0"

_uuid               : d3bf94c7-dc37-47ff-b5f2-3ca0fb506f78
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fc540c3b-8140-4cae-a262-9e64ad482638]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : 5bef7f0e-ea58-42b4-b0bf-bbe834433858
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
statistics          : {collisions=0, rx_bytes=1028561, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=10522, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 4f7628df-16f6-479b-8385-94bd509370f3
admin_state         : up
duplex              : full
ifindex             : 69
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

_uuid               : fc540c3b-8140-4cae-a262-9e64ad482638
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=380724, tx_dropped=0, tx_errors=0, tx_packets=4114}
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
    
    Simplify (a && b) || (!a && c) to just a ? b : c.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
