---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
925d29d6-84c9-4fee-b250-858ad78fa82d
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 94d9a6b5-01d3-4c17-b61a-9273cb9d9838
controller          : [081d5d34-2250-4fc2-96f6-af4cc4c56089]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [51a89304-05a9-44c3-88b3-6b26012ce0d7, 70125509-d65f-4d18-b2b2-01d2ecdfbebe, 917e611f-5a19-4440-af82-e9ee5cdfcfa3, b4912712-008b-4da1-b16b-71d7a52c2267]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 081d5d34-2250-4fc2-96f6-af4cc4c56089
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 51a89304-05a9-44c3-88b3-6b26012ce0d7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d30259bf-1bd4-48bd-a003-c23fee1a0402]
name                : "eth22"

_uuid               : 70125509-d65f-4d18-b2b2-01d2ecdfbebe
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bd09f842-4c27-4a06-b844-979f783f3ca4]
name                : "eth23"

_uuid               : b4912712-008b-4da1-b16b-71d7a52c2267
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3ce3da75-77df-4f97-97d0-e9c8768cf3ed]
name                : "br0"

_uuid               : 917e611f-5a19-4440-af82-e9ee5cdfcfa3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5d33239b-be2c-44d4-a1aa-9db59c41be92]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3ce3da75-77df-4f97-97d0-e9c8768cf3ed
admin_state         : down
duplex              : full
ifindex             : 449
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

_uuid               : bd09f842-4c27-4a06-b844-979f783f3ca4
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

_uuid               : 5d33239b-be2c-44d4-a1aa-9db59c41be92
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

_uuid               : d30259bf-1bd4-48bd-a003-c23fee1a0402
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
commit 96af668a82016d17c6300f0cfad5cd156f850545
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Sep 11 13:42:41 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Sep 11 13:42:41 2015 -0700

    ovn-northd: Minor logical flow table optimizations.
    
    There's no need to add a priority-0 &quot;drop&quot; flow, because OVN logical flow
    tables always drop non-matching packets.
    
    There's no need to add a &quot;drop&quot; flow for ingress port security on disabled
    logical ports, because no other flow would allow those packets; it's
    more efficient to omit the logical flow entirely.
    
    Finally, there's no need to add disabled logical ports to the MC_UNKNOWN
    multicast group, since packets won't be delivered to a disabled logical
    port anyway.  &#40;This is just an optimization; the packets were dropped in
    the egress pipeline anyway.&#41;
    
    Found by inspection.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
