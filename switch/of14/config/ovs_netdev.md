---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fef160b3-cba7-47bf-8790-9b483de49749
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : bd57610d-02cc-4cf1-91c9-4fc86796c388
controller          : [7e6f2fc3-f414-4376-870b-0d16c826c1e1]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [02fd82d9-e8b4-4a1d-96ab-35510e7a9dcc, 295cbc41-ca63-4402-b057-a03c9c5cb807, 8d9c67c6-caee-47d4-886b-3149e0bcb197, f8a0cee7-4927-4ea1-abd8-43a976ca095c]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7e6f2fc3-f414-4376-870b-0d16c826c1e1
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 295cbc41-ca63-4402-b057-a03c9c5cb807
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1a35ffe2-373b-43dc-aaed-ecf5f9399456]
name                : "eth23"

_uuid               : 02fd82d9-e8b4-4a1d-96ab-35510e7a9dcc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [89d4b60c-dc9c-4ca8-b756-ee5da8688c5d]
name                : "eth22"

_uuid               : 8d9c67c6-caee-47d4-886b-3149e0bcb197
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [18ab1a20-e4f9-4f6d-bf11-45be1f24cc7d]
name                : "br0"

_uuid               : f8a0cee7-4927-4ea1-abd8-43a976ca095c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4308888e-19c0-41e5-883d-6ea4878162ae]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 18ab1a20-e4f9-4f6d-bf11-45be1f24cc7d
admin_state         : down
duplex              : full
ifindex             : 61
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

_uuid               : 89d4b60c-dc9c-4ca8-b756-ee5da8688c5d
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

_uuid               : 4308888e-19c0-41e5-883d-6ea4878162ae
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

_uuid               : 1a35ffe2-373b-43dc-aaed-ecf5f9399456
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit cd159f1a82674eca96e8e2c0f184e3abac92172d
Author:     Ethan Jackson &lt;ethan@nicira.com&gt;
AuthorDate: Sat May 16 08:18:20 2015 -0700
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Tue May 19 14:47:00 2015 -0700

    dpdk: Ditch MAX_PKT_BURST macro.
    
    The MAX_PKT_BURST and NETDEV_MAX_RX_BATCH macros had a confusing
    relationship.  They basically purport to do the same thing, making it
    unclear which is the source of truth.
    
    Furthermore, while NETDEV_MAX_RX_BATCH was 256, MAX_PKT_BURST was 32,
    meaning we never process a batch larger than 32 packets further adding
    to the confusion.
    
    This patch resolves the issue by removing MAX_PKT_BURST completely,
    and shrinking the new NETDEV_MAX_BURST macro to only 32.  This should
    have no change in the execution path except shrinking a couple of
    structs and memory allocations &#40;can't hurt&#41;.
    
    Signed-off-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Acked-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>
