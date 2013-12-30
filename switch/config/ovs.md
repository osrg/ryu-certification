---
layout: default
title: ovs - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0451677d-bff3-446e-b7af-ba3fb20fe631
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
_uuid               : 3aabbde3-ebaa-4365-976f-d7d58f07f86f
controller          : [c3cb45cb-a361-4e26-8aaa-d328a5b086e3]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1811d3aa-3fae-483e-9794-f78803258851, 994969ee-3411-422c-acb5-bae5279cc655, d3955168-b088-4fe8-9200-c8bdf134874a]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : c3cb45cb-a361-4e26-8aaa-d328a5b086e3
is_connected        : true
role                : other
status              : {last_error="Connection refused", sec_since_connect="127", sec_since_disconnect="129", state=ACTIVE}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : d3955168-b088-4fe8-9200-c8bdf134874a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9c95ffee-84b8-463c-afba-a62156f40a33]
name                : "eth7"

_uuid               : 994969ee-3411-422c-acb5-bae5279cc655
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [45a12edf-d36d-44de-9575-562a5aa99bbf]
name                : "br0"

_uuid               : 1811d3aa-3fae-483e-9794-f78803258851
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d21b138d-7d0e-4b3e-97b4-340ee8b4a953]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : d21b138d-7d0e-4b3e-97b4-340ee8b4a953
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=11040, tx_dropped=0, tx_errors=0, tx_packets=119}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 9c95ffee-84b8-463c-afba-a62156f40a33
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
statistics          : {collisions=0, rx_bytes=21744, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=228, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 45a12edf-d36d-44de-9575-562a5aa99bbf
admin_state         : up
ifindex             : 59
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
commit 125bf01da3c0fba506c606ba87a2e8a8fb12d9eb
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Mon Dec 30 15:42:36 2013 -0800
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Mon Dec 30 15:42:36 2013 -0800

    tests: Make some tests more robust.
    
    These tests break if OVS internal hash function is changed.  Some of
    this is due to dependency on the order in which elements are iterated
    from hash maps, or the algorithm used is just dependent on the
    specific hash values produced for specific inputs (groups).  These
    changes make these test cases more robust, so that they will not break
    so easily due to OVS internal hash function implementation changes.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
