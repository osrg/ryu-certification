---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
030e0eb5-f51b-4298-91e3-16ce68076cec
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 98f9c631-53eb-4815-bc25-423a16d9accf
controller          : [31088622-5e45-46b3-9099-c446b9eabc83]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [7158ebb4-1427-4275-9b6a-bbca2b7478b6, 728d4369-fdc7-4fb4-8eb8-82b6abe12342, 9f160e6c-e50c-45f7-9968-25e4a1316176, e23a9dfd-6277-4b67-8ff5-3f19c1dd43b3]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 31088622-5e45-46b3-9099-c446b9eabc83
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7158ebb4-1427-4275-9b6a-bbca2b7478b6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9c3f1e03-293f-4f26-8cbd-b6ce06f0744e]
name                : "eth21"

_uuid               : 9f160e6c-e50c-45f7-9968-25e4a1316176
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1c94d3ff-9728-4ac2-8776-0f968da1c12b]
name                : "eth22"

_uuid               : 728d4369-fdc7-4fb4-8eb8-82b6abe12342
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bc87d44c-58de-415c-ae5c-23084e0cb9dc]
name                : "eth23"

_uuid               : e23a9dfd-6277-4b67-8ff5-3f19c1dd43b3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1c372a08-9d13-46ba-8682-6039d275a65e]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1c372a08-9d13-46ba-8682-6039d275a65e
admin_state         : down
duplex              : full
ifindex             : 636
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

_uuid               : bc87d44c-58de-415c-ae5c-23084e0cb9dc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5503801500, tx_dropped=0, tx_errors=0, tx_packets=3669201}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1c94d3ff-9728-4ac2-8776-0f968da1c12b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28698058125, tx_dropped=0, tx_errors=0, tx_packets=19150733}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9c3f1e03-293f-4f26-8cbd-b6ce06f0744e
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
statistics          : {collisions=0, rx_bytes=41108661551, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27448266, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 11968381be82dcfbfdd0823b7aed35d3ee3c7048
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Wed Nov 11 11:39:51 2015 -0800
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Tue Dec 1 15:29:01 2015 -0800

    ofproto-dpif: Shortcut common case in rule_check&#40;&#41;.
    
    Typically the datapath will support all available features, so check
    that first before attempting to retrieve various values out of a
    minimask as the latter doesn't need to be checked if all fields are
    supported.
    
    ct_state is an exception, because support for the bits in this field is
    not binary; only some bits are defined so far, so they must still be
    checked against the current known supported bits.
    
    Suggested-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jarno@ovn.org&gt;
</pre>
