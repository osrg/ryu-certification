---
layout: default
title: ovs - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e474f4e1-9246-4a0f-b1d9-75b646cbb292
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
_uuid               : 32d49ddf-b713-4338-a45b-30cd38995ab9
controller          : [afb8ede1-1abd-47e7-8f32-8c925a590859]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [08d57093-5c39-463e-9453-5a8733b768f1, 6b3f59be-4d64-4e06-ad71-d609a5cab2e0, c48f0dde-7e82-4a2e-888b-ccc725a133c6]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : afb8ede1-1abd-47e7-8f32-8c925a590859
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="351", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : c48f0dde-7e82-4a2e-888b-ccc725a133c6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2d0b249f-31db-4bf1-a578-d1293fc0fb54]
name                : "br0"

_uuid               : 6b3f59be-4d64-4e06-ad71-d609a5cab2e0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1efe9281-2c63-4bad-9bd4-311856af67ea]
name                : "eth8"

_uuid               : 08d57093-5c39-463e-9453-5a8733b768f1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fb578b57-5da9-4e70-8e36-b5881c20123e]
name                : "eth7"

$ sudo ovs-vsctl list Interface
_uuid               : 1efe9281-2c63-4bad-9bd4-311856af67ea
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

_uuid               : fb578b57-5da9-4e70-8e36-b5881c20123e
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

_uuid               : 2d0b249f-31db-4bf1-a578-d1293fc0fb54
admin_state         : up
ifindex             : 67
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
commit 5054d6fd32d5dd3354c1aed1bfa9fb2b7979324e
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Dec 31 11:32:16 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Dec 31 11:36:39 2013 -0800

    odp-util: Avoid null dereference in parse_8021q_onward().
    
    For parsing a mask, this code in parse_8021q_onward() always read out
    the OVS_KEY_ATTR_VLAN attribute without first checking whether it existed.
    The correct behavior, implemented by this commit, appears to be treating
    the VLAN as wildcarded and to continue parsing the flow.
    
    Bug #22312.
    Reported-by: Krishna Miriyala &lt;miriyalak@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
