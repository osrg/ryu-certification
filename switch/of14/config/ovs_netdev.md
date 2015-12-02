---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0ca5943b-3e43-4ed8-8de6-607ad959d2f9
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
_uuid               : 43bcff1e-faae-4cd0-a0dc-3bb8d4b6f7fc
controller          : [7c85b0f2-37f4-4385-b444-02ffb84f94a3]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1932bc6e-0e3d-4942-8015-9e80c423ffbc, aff4d5a8-2773-4e91-af21-a83600378002, c9beeda1-3cba-4b3f-aea9-0a1a5d09d9ad, e9797ef0-68fc-44a7-b121-ba6053c0badd]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7c85b0f2-37f4-4385-b444-02ffb84f94a3
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="16", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e9797ef0-68fc-44a7-b121-ba6053c0badd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ebbb226c-e822-4b4d-808e-ae8fb36377f4]
name                : "eth23"

_uuid               : aff4d5a8-2773-4e91-af21-a83600378002
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [abbf5898-e033-44b6-9421-6cb3570599fb]
name                : "br0"

_uuid               : c9beeda1-3cba-4b3f-aea9-0a1a5d09d9ad
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cd386d24-7d9c-4293-8dd0-3f371c6cf3d3]
name                : "eth21"

_uuid               : 1932bc6e-0e3d-4942-8015-9e80c423ffbc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [32de3094-eba1-4467-848a-3bc0e88af948]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 32de3094-eba1-4467-848a-3bc0e88af948
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28698058383, tx_dropped=0, tx_errors=0, tx_packets=19150736}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ebbb226c-e822-4b4d-808e-ae8fb36377f4
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

_uuid               : cd386d24-7d9c-4293-8dd0-3f371c6cf3d3
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
statistics          : {collisions=0, rx_bytes=41108661809, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27448269, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : abbf5898-e033-44b6-9421-6cb3570599fb
admin_state         : down
duplex              : full
ifindex             : 638
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
