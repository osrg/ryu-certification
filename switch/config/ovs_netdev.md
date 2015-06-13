---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0c676856-36ad-40f5-a6bf-e15673c6c433
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
_uuid               : 77bfa836-df0b-45ea-ae86-fc84675cac81
controller          : [94697c5b-f615-4aa7-ad8e-0c23015624a6]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [36667c34-c2d3-4b8d-8185-dc3234f097b8, 597af0d3-a652-4315-aaeb-0064f7af2cd0, 8e7d5bf6-ab0a-4a47-8c90-1c079da3573a, ee64320f-4f4b-4aa9-937b-527d494ceb56]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 94697c5b-f615-4aa7-ad8e-0c23015624a6
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 36667c34-c2d3-4b8d-8185-dc3234f097b8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [29837776-5c46-4d79-afdd-b095689db380]
name                : "br0"

_uuid               : 8e7d5bf6-ab0a-4a47-8c90-1c079da3573a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [de733d3f-2beb-443b-a119-415433b85912]
name                : "eth21"

_uuid               : 597af0d3-a652-4315-aaeb-0064f7af2cd0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [14ff608a-73b5-43e0-bb9f-58498501ecad]
name                : "eth23"

_uuid               : ee64320f-4f4b-4aa9-937b-527d494ceb56
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0e12838b-400f-44c0-954a-293831e2986b]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 14ff608a-73b5-43e0-bb9f-58498501ecad
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

_uuid               : 29837776-5c46-4d79-afdd-b095689db380
admin_state         : down
duplex              : full
ifindex             : 153
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

_uuid               : 0e12838b-400f-44c0-954a-293831e2986b
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

_uuid               : de733d3f-2beb-443b-a119-415433b85912
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
commit 1c38055de17b4ef00e12e0573fd433989309dc96
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Fri Jun 12 16:12:56 2015 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Fri Jun 12 16:12:56 2015 -0700

    ofproto: Support port mods in bundles.
    
    Add support for port mods in an OpenFlow 1.4 bundle, as required for
    the minimum support level by the OpenFlow 1.4 specification.  If the
    bundle includes port mods, it may not specify the OFPBF_ATOMIC flag.
    Port mods and flow mods in a bundle are always applied in order and
    the consecutive flow mods between port mods are made available to
    lookups atomically.
    
    Note that ovs-ofctl does not support creating bundles with port mods.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
