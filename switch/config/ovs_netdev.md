---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
bf1bdae7-93d9-494a-8d69-b497779ee436
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
_uuid               : 8f17820b-c59e-4979-bc4d-e66742d1ec69
controller          : [2470ead3-4863-43c9-8d81-15ae5ed93334]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [65b2eb66-b1e6-49e2-8518-e81efcbf6200, 945e9588-551e-4755-ae99-ea9b04782d48, d6858257-5d84-481d-b1e9-1c12ed3596e4, dfb8b6dd-5feb-4e98-a15b-c9aabde5c00d]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2470ead3-4863-43c9-8d81-15ae5ed93334
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 945e9588-551e-4755-ae99-ea9b04782d48
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [60f784ec-c4f1-48b4-b49a-1b25eb12b1ea]
name                : "eth23"

_uuid               : dfb8b6dd-5feb-4e98-a15b-c9aabde5c00d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [68e5967f-716a-4210-b88d-ee3a8089cdfa]
name                : "eth21"

_uuid               : 65b2eb66-b1e6-49e2-8518-e81efcbf6200
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [369b1ff8-1ee6-4b2e-92d5-47d4321a88c1]
name                : "eth22"

_uuid               : d6858257-5d84-481d-b1e9-1c12ed3596e4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [709b3cca-f61d-41a7-8f81-3d2d49423fa7]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 60f784ec-c4f1-48b4-b49a-1b25eb12b1ea
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

_uuid               : 369b1ff8-1ee6-4b2e-92d5-47d4321a88c1
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

_uuid               : 709b3cca-f61d-41a7-8f81-3d2d49423fa7
admin_state         : down
duplex              : full
ifindex             : 327
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

_uuid               : 68e5967f-716a-4210-b88d-ee3a8089cdfa
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
commit 6728d578f64e124d9905f1d48899226405cb85ae
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Mon Jun 29 18:01:59 2015 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Wed Aug 5 20:26:48 2015 -0700

    dpif-netdev: Translate Geneve options per-flow, not per-packet.
    
    The kernel implementation of Geneve options stores the TLV option
    data in the flow exactly as received, without any further parsing.
    This is then translated to known options for the purposes of matching
    on flow setup &#40;which will then install a datapath flow in the form
    the kernel is expecting&#41;.
    
    The userspace implementation behaves a little bit differently - it
    looks up known options as each packet is received. The reason for this
    is there is a much tighter coupling between datapath and flow translation
    and the representation is generally expected to be the same. This works
    but it incurs work on a per-packet basis that could be done per-flow
    instead.
    
    This introduces a small translation step for Geneve packets between
    datapath and flow lookup for the userspace datapath in order to
    allow the same kind of processing that the kernel does. A side effect
    of this is that unknown options are now shown when flows dumped via
    ovs-appctl dpif/dump-flows, similar to the kernel.
    
    There is a second benefit to this as well: for some operations it is
    preferable to keep the options exactly as they were received on the wire,
    which this enables. One example is that for packets that are executed from
    ofproto-dpif-upcall to the datapath, this avoids the translation of
    Geneve metadata. Since this conversion is potentially lossy &#40;for unknown
    options&#41;, keeping everything in the same format removes the possibility
    of dropping options if the packet comes back up to userspace and the
    Geneve option translation table has changed. To help with these types of
    operations, most functions can understand both formats of data and seamlessly
    do the right thing.
    
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
