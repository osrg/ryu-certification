---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a6dace1e-d0dc-4537-a65d-e27005fb72ad
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 462edcd3-fce2-450b-9ffe-7081d42b2aab
controller          : [f0386a7d-e123-4f22-a521-12e9c8e9da0c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2a54b6ec-4f5b-4e2b-a532-244e5e1b8ba7, 32ac0557-744d-4bbc-92e0-633784ffee44, a0fcdfb7-cd43-483e-991f-6f63da55297c, a5dde905-b86d-41c9-a0ff-c5e38163b2a7]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f0386a7d-e123-4f22-a521-12e9c8e9da0c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2a54b6ec-4f5b-4e2b-a532-244e5e1b8ba7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e799ffe4-0fdf-45ff-b5e4-6a0ef576ccc1]
name                : "eth21"

_uuid               : a5dde905-b86d-41c9-a0ff-c5e38163b2a7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [13f7d9f8-ae95-4985-9803-3c5573e52dae]
name                : "eth22"

_uuid               : 32ac0557-744d-4bbc-92e0-633784ffee44
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a9e4dc1a-15f2-4e59-84f5-60194b9d81a9]
name                : "eth23"

_uuid               : a0fcdfb7-cd43-483e-991f-6f63da55297c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5859b29d-6afc-4e77-8c19-3e693f18e1c1]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e799ffe4-0fdf-45ff-b5e4-6a0ef576ccc1
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

_uuid               : 13f7d9f8-ae95-4985-9803-3c5573e52dae
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

_uuid               : 5859b29d-6afc-4e77-8c19-3e693f18e1c1
admin_state         : down
duplex              : full
ifindex             : 194
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

_uuid               : a9e4dc1a-15f2-4e59-84f5-60194b9d81a9
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
commit 9ad11dbe4c40ddbd388b8d51c416d89dda0cf380
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Fri Jun 12 12:49:23 2015 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Thu Jun 25 11:08:58 2015 -0700

    pkt-metadata: Avoid introducing overhead for userspace tunnels.
    
    The addition of Geneve metadata requires a large amount of additional
    space to handle the maximum set of options. In most cases, this is
    not a big deal since it is only temporary storage on the stack or
    can be automatically stripped out for miniflows. However, userspace
    tunnels need to deal with this on a per-packet basis, so we should
    avoid introducing additional overhead if possible. Two small changes
    are aimed at this:
    
     * Move struct flow_tnl to the end of the packet metadata. Since
       the Geneve metadata is already at the end of flow_tnl and pkt_metadata
       is at the end of struct dp_packet, this avoids putting a large
       amount metadata &#40;which might be empty&#41; in hot cache lines.
    
     * Only push the new metadata into a miniflow if any options are present
       during miniflow_extract&#40;&#41;. This does not necessarily provide the
       most fine-grained flow generation but it is a quick check and
       the userspace implementation of Geneve does not currently support
       options anyways.
    
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
