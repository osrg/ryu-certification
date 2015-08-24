---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
09326e93-e4a3-47e6-b06c-0e260bece25e
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 273ec6b1-76ac-4b15-bfbc-1d2d2410edbc
controller          : [0659e665-0dad-4074-a519-1081bc5ee43d]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [18af721b-1955-4878-b4d0-25d53a0b2110, a1dc8e4d-a388-4238-9cc0-91d4220daf3f, b5a6af7f-0831-4b9b-9e75-3d072ff5159e, c7750be3-243a-4616-9f65-9278a302a5fa]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0659e665-0dad-4074-a519-1081bc5ee43d
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a1dc8e4d-a388-4238-9cc0-91d4220daf3f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c7b738eb-25cd-4507-84b5-9e631aa11a62]
name                : "eth22"

_uuid               : 18af721b-1955-4878-b4d0-25d53a0b2110
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [04246cc7-1755-4e6c-9a90-f0af6d12a334]
name                : "br0"

_uuid               : b5a6af7f-0831-4b9b-9e75-3d072ff5159e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c39df7aa-9453-4c76-ac70-f28a16f2dba5]
name                : "eth21"

_uuid               : c7750be3-243a-4616-9f65-9278a302a5fa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7c0fa447-849a-4a35-8999-67a33dfb0fa7]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c39df7aa-9453-4c76-ac70-f28a16f2dba5
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

_uuid               : c7b738eb-25cd-4507-84b5-9e631aa11a62
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

_uuid               : 7c0fa447-849a-4a35-8999-67a33dfb0fa7
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

_uuid               : 04246cc7-1755-4e6c-9a90-f0af6d12a334
admin_state         : down
duplex              : full
ifindex             : 385
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
