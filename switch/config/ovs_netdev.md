---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a393b076-84e9-4fb9-b083-ae0ada43413c
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7e35639d-d76a-4f92-ba13-da356ed1dee1
controller          : [8d071f11-d0e9-4e11-9266-511432b136a6]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0665c036-6777-436d-91b9-cfd953cb2944, c3d30db8-74ab-4b3b-92a9-c6314866264d, ebfe4ece-f065-4c01-84d5-c43672d5a1ae, fbf82f94-49bb-4c36-99b0-9f7b9dbbaf43]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8d071f11-d0e9-4e11-9266-511432b136a6
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c3d30db8-74ab-4b3b-92a9-c6314866264d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [14f5a3bd-51ee-416b-9d34-083876253251]
name                : "br0"

_uuid               : fbf82f94-49bb-4c36-99b0-9f7b9dbbaf43
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5adb30ba-eae4-46a5-9ee3-cf68d339dcce]
name                : "eth21"

_uuid               : ebfe4ece-f065-4c01-84d5-c43672d5a1ae
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2cee42fd-9a61-46fb-b241-c12028cd4fd0]
name                : "eth23"

_uuid               : 0665c036-6777-436d-91b9-cfd953cb2944
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b93eb0b7-f7f6-486c-8653-e128bc92eb8d]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 14f5a3bd-51ee-416b-9d34-083876253251
admin_state         : down
duplex              : full
ifindex             : 383
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

_uuid               : 2cee42fd-9a61-46fb-b241-c12028cd4fd0
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

_uuid               : 5adb30ba-eae4-46a5-9ee3-cf68d339dcce
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

_uuid               : b93eb0b7-f7f6-486c-8653-e128bc92eb8d
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
commit 053df7bda62b6892029b2f9306f3d0481b69dea9
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Aug 20 17:07:40 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Aug 24 11:01:00 2015 -0700

    ofp-util: For OF1.0, don't wildcard PCP field when 802.1Q header absent.
    
    OpenFlow 1.0.1 says:
    
        The dl_vlan_pcp field must be ignored when the OFPFW_DL_VLAN wildcard
        bit is set or when the dl_vlan value is set to OFP_VLAN_NONE.  Fields
        that are ignored don’t need to be wildcarded and should be set to 0.
    
    Previously, OVS wildcarded the PCP field when dl_vlan was OFP_VLAN_NONE,
    but this commit changes the behavior to that suggested above: the PCP
    field should not be wildcarded &#40;and should be set to 0, but the code
    already did that&#41;.
    
    This commit only changes the translation from OVS's internal flow format
    to the OpenFlow 1.0 wire format.  Translation in the other direction and
    to other formats is unaffected.
    
    Found by OFTest.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
