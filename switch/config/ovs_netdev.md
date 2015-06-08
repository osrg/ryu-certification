---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6e6d4a69-01e8-41f8-965e-b039f3faa212
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
_uuid               : d6eec19a-0f5b-4674-8ae0-410cf3c1eb94
controller          : [2874c0ed-1a60-4a24-857e-f3dce2a7fdb8]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [33b2b72b-27e5-4544-94b8-11b32054b361, 5b714967-ceaa-4dd3-90fb-5c30eb5a4319, 61f5e164-d398-465f-b9d5-3163dec41856, c883be3c-4450-4545-8774-3b80b7130e2e]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2874c0ed-1a60-4a24-857e-f3dce2a7fdb8
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 61f5e164-d398-465f-b9d5-3163dec41856
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [da3ecf51-6056-4815-81e6-85019b8036db]
name                : "eth21"

_uuid               : c883be3c-4450-4545-8774-3b80b7130e2e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f87d7c87-6d87-4765-9c11-46d30037b34b]
name                : "br0"

_uuid               : 5b714967-ceaa-4dd3-90fb-5c30eb5a4319
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d4215bc8-781e-4e02-8782-d25c322cded1]
name                : "eth23"

_uuid               : 33b2b72b-27e5-4544-94b8-11b32054b361
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9b5ff434-0523-4c5a-bd55-db73d6f05d68]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d4215bc8-781e-4e02-8782-d25c322cded1
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

_uuid               : 9b5ff434-0523-4c5a-bd55-db73d6f05d68
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

_uuid               : da3ecf51-6056-4815-81e6-85019b8036db
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

_uuid               : f87d7c87-6d87-4765-9c11-46d30037b34b
admin_state         : down
duplex              : full
ifindex             : 118
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
commit 50dcbd8ed473210e6d2aa44f28843fb417416397
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Fri May 15 17:03:17 2015 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Mon Jun 8 10:17:58 2015 -0700

    ofp-util: Convert flow_metadata to match structure.
    
    We have a special flow_metadata structure to represent the parts
    of a packet that aren't carried in the payload itself. This is
    used in the case where we need to send the packet as a Packet In
    to an OpenFlow controller. This is a subset of the more general
    struct flow.
    
    In practice, almost all operations we do on this structure involve
    converting it to or from a match or have code that is the same as
    a match. Serialization to NXM and back is done as a match. There
    is special flow_metadata formatting code that is almost identical
    to match formatting.
    
    The uses for struct flow_metadata aren't performance critical
    when it comes to memory, so we can save quite a bit of code by
    just using a match structure directly instead. In addition, as
    metadata increases and becomes more complex &#40;Geneve options require
    some special handling beyond just additional fields&#41;, using the
    match structure means we only have to do this work in one place.
    
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
