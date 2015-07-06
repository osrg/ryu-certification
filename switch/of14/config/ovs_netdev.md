---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3e79a2ba-d410-4199-9b45-385c5c8286ba
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7f8e8889-a01a-41b4-aa4b-eb3f6fbef478
controller          : [99a47f92-9828-4a3a-8a95-ac678d285678]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1477e57c-bb6c-4abd-a591-8586dda112f0, 91c903ae-e30c-44b5-b3d0-47f21cf6c57b, db52b1df-7e0c-4e8d-8db4-ca0bf276b0cb, fe06088c-5fda-4391-86ea-b787a50e8034]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 99a47f92-9828-4a3a-8a95-ac678d285678
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1477e57c-bb6c-4abd-a591-8586dda112f0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [80afa524-3d1c-4b84-8c19-f73d736e51fc]
name                : "eth23"

_uuid               : fe06088c-5fda-4391-86ea-b787a50e8034
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1ecb84ca-0ff7-4144-bfca-2f2d249a0ffa]
name                : "br0"

_uuid               : 91c903ae-e30c-44b5-b3d0-47f21cf6c57b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c7fd25b0-7ec9-4ede-86e2-98e388abc1d5]
name                : "eth22"

_uuid               : db52b1df-7e0c-4e8d-8db4-ca0bf276b0cb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3ad40d12-15c6-496e-9d01-0af302502c8f]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 80afa524-3d1c-4b84-8c19-f73d736e51fc
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

_uuid               : c7fd25b0-7ec9-4ede-86e2-98e388abc1d5
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

_uuid               : 1ecb84ca-0ff7-4144-bfca-2f2d249a0ffa
admin_state         : down
duplex              : full
ifindex             : 227
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

_uuid               : 3ad40d12-15c6-496e-9d01-0af302502c8f
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit bd53aa1723a007415d26fdd8fb7da05acc06aad0
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Mon Jul 6 11:45:54 2015 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Mon Jul 6 11:46:34 2015 -0700

    classifier: Make versioning more explicit.
    
    Now that struct cls_match has 'add_version' the 'version' in cls_match
    was largely redundant.  Remove 'version' from struct cls_rule, and add
    it to function prototypes that need it.  This makes versioning more
    explicit &#40;or less indirect&#41; in the API.
    
    Suggested-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
