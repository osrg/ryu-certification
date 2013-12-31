---
layout: default
title: ovs - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8f126f49-53ac-4eb1-b4ec-6e6b529733b6
    Bridge "br0"
        Controller "tcp:10.24.150.30"
            is_connected: true
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth7"
            Interface "eth7"
        Port "eth8"
            Interface "eth8"

$ sudo ovs-vsctl list Bridge
_uuid               : 3df9532d-a164-4d32-989c-65482e1a7a06
controller          : [508d5d71-03ec-4e7f-b269-310c94473c29]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [125fb5d6-68fa-4d6a-acd2-d9ac9026e460, 7c1988cf-8499-4bc1-9d68-30cf79c627a5, 9c362133-99c7-402d-991b-1f6249337bfc]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 508d5d71-03ec-4e7f-b269-310c94473c29
is_connected        : true
role                : other
status              : {last_error="Connection refused", sec_since_connect="126", sec_since_disconnect="128", state=ACTIVE}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 125fb5d6-68fa-4d6a-acd2-d9ac9026e460
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [77a368c0-50a1-4e73-a04e-6785fd135d77]
name                : "br0"

_uuid               : 7c1988cf-8499-4bc1-9d68-30cf79c627a5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ad59295a-bae8-419e-a905-3a0db4d3014a]
name                : "eth7"

_uuid               : 9c362133-99c7-402d-991b-1f6249337bfc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4bc98664-b16e-4c2c-a2d9-815d4ca33dad]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : 77a368c0-50a1-4e73-a04e-6785fd135d77
admin_state         : up
ifindex             : 65
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

_uuid               : 4bc98664-b16e-4c2c-a2d9-815d4ca33dad
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=11222, tx_dropped=0, tx_errors=0, tx_packets=121}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : ad59295a-bae8-419e-a905-3a0db4d3014a
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
statistics          : {collisions=0, rx_bytes=22189, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=233, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 758c456df570a1af1d9e913d50a3478785663e66
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Mon Dec 30 15:58:58 2013 -0800
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Mon Dec 30 16:52:43 2013 -0800

    dpif: Use explicit packet metadata.
    
    This helps reduce confusion about when a flow is a flow and when it is
    just metadata.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
