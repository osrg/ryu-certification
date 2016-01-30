---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ca99cd0b-fd0c-451e-93eb-7a160b65df4e
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f3c458a9-29c3-43cf-b7b8-be206943e7b4
controller          : [5c29b7bc-9dd6-469e-b1be-f55288072b53]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [7cdf114e-793e-4374-ab44-d27a4d60b077, d1be561e-af2f-4559-8e7a-d68bf077164d, d96b7e43-90eb-47a7-9d3a-e1e3e1286dfb, eed2241c-0a35-40d3-ad51-bcdf874db00b]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5c29b7bc-9dd6-469e-b1be-f55288072b53
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : eed2241c-0a35-40d3-ad51-bcdf874db00b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2ffcfed0-c17c-471b-a170-462dd50ee75b]
name                : "eth23"

_uuid               : d1be561e-af2f-4559-8e7a-d68bf077164d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [292835c2-410f-4e52-a58d-af1a686d8efa]
name                : "br0"

_uuid               : 7cdf114e-793e-4374-ab44-d27a4d60b077
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bc522713-37a4-4274-945f-120b63d02341]
name                : "eth22"

_uuid               : d96b7e43-90eb-47a7-9d3a-e1e3e1286dfb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f34120a9-d3ad-41ae-942f-009db6971fb2]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2ffcfed0-c17c-471b-a170-462dd50ee75b
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

_uuid               : f34120a9-d3ad-41ae-942f-009db6971fb2
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
statistics          : {collisions=0, rx_bytes=44502304132, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29729766, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 292835c2-410f-4e52-a58d-af1a686d8efa
admin_state         : down
duplex              : full
ifindex             : 750
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

_uuid               : bc522713-37a4-4274-945f-120b63d02341
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30225122974, tx_dropped=0, tx_errors=0, tx_packets=20178075}
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
