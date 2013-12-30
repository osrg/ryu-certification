---
layout: default
title: ovs - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2c45b793-4b99-49b6-8750-34bd38ede60c
    Bridge "br0"
        Controller "tcp:10.24.150.30"
            is_connected: true
        fail_mode: secure
        Port "eth8"
            Interface "eth8"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth7"
            Interface "eth7"

$ sudo ovs-vsctl list Bridge
_uuid               : f93a6f31-7b6f-4a17-a40c-1185d669929a
controller          : [93cd66eb-366c-45e2-8b82-bb6a333fa2c1]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [455e24e9-b38e-4097-8766-77370bfce1f3, 6ff14226-4135-461f-af9a-79b71296bfff, b08857a6-51ed-49ad-a373-d6b975b3ede4]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 93cd66eb-366c-45e2-8b82-bb6a333fa2c1
is_connected        : true
role                : other
status              : {last_error="Connection refused", sec_since_connect="122", sec_since_disconnect="124", state=ACTIVE}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 455e24e9-b38e-4097-8766-77370bfce1f3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [96c3ed46-e581-4410-9cfe-39fa2926dd94]
name                : "eth8"

_uuid               : 6ff14226-4135-461f-af9a-79b71296bfff
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7ba982f1-ffcf-462b-9ac3-5ea71150354d]
name                : "br0"

_uuid               : b08857a6-51ed-49ad-a373-d6b975b3ede4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [043479c1-fb02-4488-b477-c7db0b489efc]
name                : "eth7"

$ sudo ovs-vsctl list Interface
_uuid               : 7ba982f1-ffcf-462b-9ac3-5ea71150354d
admin_state         : up
ifindex             : 55
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

_uuid               : 043479c1-fb02-4488-b477-c7db0b489efc
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
statistics          : {collisions=0, rx_bytes=21528, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=225, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 96c3ed46-e581-4410-9cfe-39fa2926dd94
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10964, tx_dropped=0, tx_errors=0, tx_packets=118}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ae6bde49ab95b77aa9d6dc84fdcb3d71b3d95a5c
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Mon Dec 30 14:21:40 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Dec 30 14:22:10 2013 -0800

    bridge: Fix reversed string parsing in bridge_configure_flow_miss_model().
    
    This commit fixes a command matching error introduced by commit
    7155fa52f (ofproto-dpif: Add force-miss-model configuration).
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
