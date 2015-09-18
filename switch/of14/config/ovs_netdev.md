---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fe1c9d4e-1b5f-498c-bbc7-d560757da53f
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : fc830b51-4aba-40b2-92f2-e2ff53f97ced
controller          : [2931d5e1-80b9-4273-9f7f-17d8590d1ec8]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3bc45de3-c25b-4e44-8634-8da2a4d95229, 44b5a9b0-13b5-4ba9-87df-f0f9ef872ec8, 451fc3b4-73f6-498f-bee4-02bfa4f4f852, dd97b6d5-bd38-4ddd-b90a-e4aa0cf87082]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2931d5e1-80b9-4273-9f7f-17d8590d1ec8
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 44b5a9b0-13b5-4ba9-87df-f0f9ef872ec8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d421efc1-3942-455c-a1bf-3f97d3ab811d]
name                : "br0"

_uuid               : 451fc3b4-73f6-498f-bee4-02bfa4f4f852
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3f5a40b1-520b-445d-83db-9bd0c25f9232]
name                : "eth21"

_uuid               : dd97b6d5-bd38-4ddd-b90a-e4aa0cf87082
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [917dd3a4-9658-4feb-8840-ce68ef624a24]
name                : "eth22"

_uuid               : 3bc45de3-c25b-4e44-8634-8da2a4d95229
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1ac84d47-c06b-4b8e-8770-038aee7aa993]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 917dd3a4-9658-4feb-8840-ce68ef624a24
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

_uuid               : 3f5a40b1-520b-445d-83db-9bd0c25f9232
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

_uuid               : d421efc1-3942-455c-a1bf-3f97d3ab811d
admin_state         : down
duplex              : full
ifindex             : 475
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

_uuid               : 1ac84d47-c06b-4b8e-8770-038aee7aa993
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
commit cee06621d90f0a30b16735e40094918a38e2d010
Author:     Chris J Arges &lt;chris.j.arges@canonical.com&gt;
AuthorDate: Fri Sep 18 13:34:22 2015 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Fri Sep 18 13:40:29 2015 -0700

    datapath: Backport &quot;openvswitch: allocate nr_node_ids flow_stats instead of num_possible_nodes&quot;
    
    Upstream commit:
        openvswitch: allocate nr_node_ids flow_stats instead of num_possible_nodes
    
        Some architectures like POWER can have a NUMA node_possible_map that
        contains sparse entries. This causes memory corruption with openvswitch
        since it allocates flow_cache with a multiple of num_possible_nodes&#40;&#41; and
        assumes the node variable returned by for_each_node will index into
        flow-&gt;stats[node].
    
        Use nr_node_ids to allocate a maximal sparse array instead of
        num_possible_nodes&#40;&#41;.
    
        The crash was noticed after 3af229f2 was applied as it changed the
        node_possible_map to match node_online_map on boot.
        Fixes: 3af229f2071f5b5cb31664be6109561fbe19c861
    
        Signed-off-by: Chris J Arges &lt;chris.j.arges@canonical.com&gt;
        Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
        Acked-by: Nishanth Aravamudan &lt;nacc@linux.vnet.ibm.com&gt;
        Signed-off-by: David S. Miller &lt;davem@davemloft.net&gt;
    
    Upstream: bac541e4631&#40;&quot;&quot;openvswitch: allocate nr_node_ids flow_stats
    instead of num_possible_nodes&quot;&#41;
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
