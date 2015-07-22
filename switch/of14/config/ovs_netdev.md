---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
eb3fb1e5-1362-4e79-816f-13cfc01a5aaa
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b29db51d-36ee-4e9e-a92a-ed043812ff8e
controller          : [15677793-1f27-4ee5-8462-e1ce050d3907]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [058e7abb-3f9a-41a7-937c-c62a3994d4de, 3076b0cd-fb2b-4b36-a058-361c75e69e6c, 311d55db-e7ae-4230-9e38-7c3d8010564f, 51bea5ab-f4c5-4c97-823d-83e2d85ff68f]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 15677793-1f27-4ee5-8462-e1ce050d3907
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3076b0cd-fb2b-4b36-a058-361c75e69e6c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [642647e7-21b8-4459-b72d-240575c7d171]
name                : "eth23"

_uuid               : 311d55db-e7ae-4230-9e38-7c3d8010564f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b5151612-022d-40a0-b399-9b7ab0917516]
name                : "eth21"

_uuid               : 51bea5ab-f4c5-4c97-823d-83e2d85ff68f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b3adf656-9692-46ec-808c-58ee15e69857]
name                : "eth22"

_uuid               : 058e7abb-3f9a-41a7-937c-c62a3994d4de
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9d035691-2b14-41fe-bf65-7eb56ec94d97]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9d035691-2b14-41fe-bf65-7eb56ec94d97
admin_state         : down
duplex              : full
ifindex             : 277
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

_uuid               : b3adf656-9692-46ec-808c-58ee15e69857
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

_uuid               : b5151612-022d-40a0-b399-9b7ab0917516
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

_uuid               : 642647e7-21b8-4459-b72d-240575c7d171
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
commit 33b2ad88ef3d02b79517d0f4e387654fce0da41d
Author:     Chris J Arges &lt;chris.j.arges@canonical.com&gt;
AuthorDate: Wed Jul 22 04:39:11 2015 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Wed Jul 22 12:54:00 2015 -0700

    datapath: allocate nr_node_ids flow_stats instead of num_possible_nodes
    
    Some architectures like POWER can have a NUMA node_possible_map that
    contains sparse entries. This causes memory corruption with openvswitch
    since it allocates flow_cache with a multiple of num_possible_nodes&#40;&#41;
    and
    assumes the node variable returned by for_each_node will index into
    flow-&gt;stats[node].
    
    Use nr_node_ids to allocate a maximal sparse array instead of
    num_possible_nodes&#40;&#41;.
    
    The crash was noticed after 3af229f2 was applied as it changed the
    node_possible_map to match node_online_map on boot.
    Fixes: 3af229f2071f5b5cb31664be6109561fbe19c861
    
    Signed-off-by: Chris J Arges &lt;chris.j.arges@canonical.com&gt;
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
