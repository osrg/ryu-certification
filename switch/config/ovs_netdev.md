---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2ff340d9-60cd-4616-a7c5-14911c040889
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 01bf72f0-68a0-4694-80b6-80ad494cd5e3
controller          : [1960bb48-f582-4b65-b482-3f91c12a704c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1f2e7199-ff2c-48e6-ae68-b9f71a9dfa28, c388c339-94fe-412f-bc72-ecc7e2aacff4, e8a29c2d-bf12-4eec-a842-d2bf08e5bde3, ed2770a0-1c8d-4bb4-b6d0-dacc9a1d1f83]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 1960bb48-f582-4b65-b482-3f91c12a704c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ed2770a0-1c8d-4bb4-b6d0-dacc9a1d1f83
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [44b8a494-b6d2-4763-b49a-e09e8c3ddbe9]
name                : "eth21"

_uuid               : c388c339-94fe-412f-bc72-ecc7e2aacff4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b3f53f38-6ac4-4e93-9757-68db4c839339]
name                : "eth22"

_uuid               : 1f2e7199-ff2c-48e6-ae68-b9f71a9dfa28
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [600f43f2-3d09-4206-b268-ff65cff50ec8]
name                : "br0"

_uuid               : e8a29c2d-bf12-4eec-a842-d2bf08e5bde3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [45f01ea6-2c4c-49b9-8b15-527c6264b0ac]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b3f53f38-6ac4-4e93-9757-68db4c839339
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30225122716, tx_dropped=0, tx_errors=0, tx_packets=20178072}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 44b8a494-b6d2-4763-b49a-e09e8c3ddbe9
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
statistics          : {collisions=0, rx_bytes=44502303874, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29729763, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 600f43f2-3d09-4206-b268-ff65cff50ec8
admin_state         : down
duplex              : full
ifindex             : 748
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

_uuid               : 45f01ea6-2c4c-49b9-8b15-527c6264b0ac
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=8047797000, tx_dropped=0, tx_errors=0, tx_packets=5365198}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9167fc1ae524e6ef33e706daf38e77af9188d8d2
Author:     Jarno Rajahalme &lt;jarno@ovn.org&gt;
AuthorDate: Fri Jan 29 17:28:08 2016 -0800
Commit:     Jarno Rajahalme &lt;jarno@ovn.org&gt;
CommitDate: Fri Jan 29 17:28:08 2016 -0800

    ofproto-dpif-xlate: Remove obsolete special case.
    
    Bond recirculation used to insert a special rule that jumped from the
    internal table to table 0 using GOTO_TABLE.  Since the introduction of
    the ofproto-dpif-rid this has not been necessary any more, so we can
    remove the special case that allowed GOTO_TABLE to go backwards in
    that case.
    
    Signed-off-by: Jarno Rajahalme &lt;jarno@ovn.org&gt;
</pre>
