---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e3556654-afcc-4451-9e26-4962064190c7
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 2d655855-4ffd-460e-853c-515ffcab7280
controller          : [513cb72d-e9b3-4e47-9574-df1f98bde1d5]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2ce752e6-4f66-4c6e-8a70-0b319adc107f, 3923aa94-c782-4889-acd1-f27f631738b2, 68f5842d-1390-442f-8673-672b8b291201, 84cc99dd-21c8-4f02-babf-b8cd952ebb63]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 513cb72d-e9b3-4e47-9574-df1f98bde1d5
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3923aa94-c782-4889-acd1-f27f631738b2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1b07166a-4a1f-4f43-8a7b-7893f1556083]
name                : "eth23"

_uuid               : 68f5842d-1390-442f-8673-672b8b291201
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6f8fa36b-28b9-4322-acb8-9e2f5a2a37cf]
name                : "eth22"

_uuid               : 84cc99dd-21c8-4f02-babf-b8cd952ebb63
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [92fc2508-fc5d-4734-8d1f-9b3ed4ae41cf]
name                : "eth21"

_uuid               : 2ce752e6-4f66-4c6e-8a70-0b319adc107f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [335a9932-49b7-4104-b51d-4be052bd0be3]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 92fc2508-fc5d-4734-8d1f-9b3ed4ae41cf
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
statistics          : {collisions=0, rx_bytes=24024581534, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16026376, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1b07166a-4a1f-4f43-8a7b-7893f1556083
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1176922500, tx_dropped=0, tx_errors=0, tx_packets=784615}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 335a9932-49b7-4104-b51d-4be052bd0be3
admin_state         : down
duplex              : full
ifindex             : 479
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

_uuid               : 6f8fa36b-28b9-4322-acb8-9e2f5a2a37cf
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18089315792, tx_dropped=0, tx_errors=0, tx_packets=12064077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 449b81311336977d874f80adde9c275dc67e0f8c
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Fri Sep 18 17:47:37 2015 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Fri Sep 18 17:47:37 2015 -0700

    dpif-netdev: Exact match non-presence of vlans.
    
    The Netlink encoding of datapath flow keys cannot express wildcarding
    the presence of a VLAN tag. Instead, a missing VLAN tag is interpreted
    as exact match on the fact that there is no VLAN.  This makes reading
    datapath flow dumps confusing, since for everything else, a missing
    key value means that the corresponding key was wildcarded.
    
    Unless we refactor a lot of code that translates between Netlink and
    struct flow representations, we have to do the same in the userspace
    datapath.  This makes at least the flow install logs show that the
    vlan_tci field is matched to zero.  However, the datapath flow dumps
    remain as they were before, as they are performed using the netlink
    format.
    
    Add a test to verify that packet with a vlan will not match a rule
    that may seem wildcarding the presence of the vlan tag.  Applying this
    test without the userspace datapath modification showed that the
    userspace datapath failed to create a new datapath flow for the VLAN
    packet before this patch.
    
    Reported-by: Tony van der Peet &lt;tony.vanderpeet@gmail.com&gt;
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
