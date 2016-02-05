---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
81f5a8fe-61b1-4a20-8401-97e135a8f54f
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f743e904-92e6-49b4-a009-d2264fee274e
controller          : [24389ab1-2749-4301-825e-0e4d97552dd2]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [31fe7bee-5a20-471a-8a2a-367bbabe034d, 397694ff-e7b7-47c8-92f0-21feb0ee43f3, 6c50c62f-d7a9-44dd-8159-c33cf49ef55e, edbf94c8-9a02-4b94-9d43-b9218d524d7e]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 24389ab1-2749-4301-825e-0e4d97552dd2
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : edbf94c8-9a02-4b94-9d43-b9218d524d7e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [73aed6e5-2a2a-4e04-8770-e527869e8a69]
name                : "eth23"

_uuid               : 31fe7bee-5a20-471a-8a2a-367bbabe034d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [40105ed9-c4df-4944-8176-7b16bd6c3704]
name                : "eth21"

_uuid               : 6c50c62f-d7a9-44dd-8159-c33cf49ef55e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [812f0bf3-ba3b-47de-9d0b-d3f4e9ae759f]
name                : "eth22"

_uuid               : 397694ff-e7b7-47c8-92f0-21feb0ee43f3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1d6531d9-8060-45e3-8651-583928df24b2]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1d6531d9-8060-45e3-8651-583928df24b2
admin_state         : down
duplex              : full
ifindex             : 768
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

_uuid               : 40105ed9-c4df-4944-8176-7b16bd6c3704
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
statistics          : {collisions=0, rx_bytes=45087364329, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30123092, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 73aed6e5-2a2a-4e04-8770-e527869e8a69
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=8486202000, tx_dropped=0, tx_errors=0, tx_packets=5657468}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 812f0bf3-ba3b-47de-9d0b-d3f4e9ae759f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30488565131, tx_dropped=0, tx_errors=0, tx_packets=20355304}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 8c0fae89d469220de42106cb62bddda4986b5583
Author:     Numan Siddique &lt;nusiddiq@redhat.com&gt;
AuthorDate: Thu Feb 4 20:11:31 2016 +0530
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Fri Feb 5 10:57:03 2016 -0500

    ovn-northd: Revert &quot;ovn-northd: Only run idl loop if something changed&quot;
    
    This reverts f20396e051ea4fd623bfc022cc78d9bd52a850e5
    
    f20396e.. was required to fix the failing ovn-sbctl testsuites.
    commit fb496f92ca1eeead8760b5cdfd857165f64deadf addresses these failing
    test cases in a proper way.
    
    With commit f20396e.. its possible that commit to the southbound db is
    delayed. When ovnnb_db_run is called, and if ctx-&gt;ovnsb_txn is NULL,
    ovnnb_db_run returns immediately without generating the logical flows.
    ovnnb_db_run is not called again until the northbound db seqno changes.
    
    Signed-off-by: Numan Siddique &lt;nusiddiq@redhat.com&gt;
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
</pre>
