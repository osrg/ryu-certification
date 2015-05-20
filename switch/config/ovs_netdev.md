---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
15b759ca-1f87-4463-b271-4919a1d3a204
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 50bd7145-3ea6-49e6-ba92-2f3e12c5d707
controller          : [53d821fd-4562-4e27-96b5-095ee990b11b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [21145fab-1140-42c6-a6f4-68e1f1a243ea, 816ef61f-ff57-41d4-bbf7-507713dd00fb, d89dc84f-56c3-4401-a1c2-bc6e58cd350e, eafc309f-35a7-4653-b088-e69e7c08781d]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 53d821fd-4562-4e27-96b5-095ee990b11b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d89dc84f-56c3-4401-a1c2-bc6e58cd350e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3d1b66cf-24ca-460a-9cfe-aee21442e7af]
name                : "br0"

_uuid               : 21145fab-1140-42c6-a6f4-68e1f1a243ea
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [39d282be-65b1-41c9-bacf-ee31527bb966]
name                : "eth23"

_uuid               : eafc309f-35a7-4653-b088-e69e7c08781d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [83d2540a-a2a7-4cc9-9bd8-4ee01016ae82]
name                : "eth21"

_uuid               : 816ef61f-ff57-41d4-bbf7-507713dd00fb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c6f74974-5691-44ad-ac5d-de46ea822375]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c6f74974-5691-44ad-ac5d-de46ea822375
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

_uuid               : 83d2540a-a2a7-4cc9-9bd8-4ee01016ae82
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

_uuid               : 39d282be-65b1-41c9-bacf-ee31527bb966
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

_uuid               : 3d1b66cf-24ca-460a-9cfe-aee21442e7af
admin_state         : down
duplex              : full
ifindex             : 59
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
