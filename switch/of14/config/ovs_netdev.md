---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6967814c-5f53-470f-b8ed-1a11e3a8e550
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d9be1113-d3a2-4785-8951-91cd3cba3222
controller          : [555c58d7-e2ce-4a0f-a74c-0cbb930bbe64]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [06f16e08-aec7-472d-81af-dc3c07b9e697, 0c95f799-af44-4a76-9182-67c169c202d6, 6e4a6357-51bb-417f-9ec5-f9d1990af60e, e55d94d5-a83d-4013-984b-b3841d12863a]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 555c58d7-e2ce-4a0f-a74c-0cbb930bbe64
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 06f16e08-aec7-472d-81af-dc3c07b9e697
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b2ee239a-ada6-4dc3-aa5b-456cdf8aba81]
name                : "eth23"

_uuid               : 0c95f799-af44-4a76-9182-67c169c202d6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d8d166a6-a9a0-4c07-b5c7-5c1408db1d29]
name                : "eth22"

_uuid               : e55d94d5-a83d-4013-984b-b3841d12863a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8538c988-20a9-4575-a5e2-e2ac91ff5fc6]
name                : "br0"

_uuid               : 6e4a6357-51bb-417f-9ec5-f9d1990af60e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f5b8ac4f-fda2-49c8-846c-e0594457f422]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8538c988-20a9-4575-a5e2-e2ac91ff5fc6
admin_state         : down
duplex              : full
ifindex             : 142
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

_uuid               : d8d166a6-a9a0-4c07-b5c7-5c1408db1d29
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

_uuid               : b2ee239a-ada6-4dc3-aa5b-456cdf8aba81
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

_uuid               : f5b8ac4f-fda2-49c8-846c-e0594457f422
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
commit db5076eee46e5ad4d67dc02b902c9b4aaeb190a4
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Fri Jun 5 14:03:12 2015 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Wed Jun 10 13:19:34 2015 -0700

    ovs-ofctl: Add bundle support and unit testing.
    
    All existing ovs-ofctl flow mod commands now take an optional
    '--bundle' argument, which executes the flow mods as a single
    transaction.  OpenFlow 1.4+ is implicitly assumed when '--bundle' is
    specified.
    
    ovs-ofctl 'add-flow' and 'add-flows' commands now accept flow
    specifications that start with an optional 'add', 'modify', 'delete',
    'modify_strict', or 'delete_strict' keyword, so that arbitrary flow
    table modifications may be specified.  For backwards compatibility, a
    missing keyword is treated as an 'add'.  With the new '--bundle'
    option all the modifications are executed as a single transaction
    using an OpenFlow 1.4 bundle.
    
    OpenFlow 1.4 requires bundles to support at least flow and port mods.
    This implementation does not yet support port mods in bundles.
    
    Another restriction is that the atomic transactions are not yet
    supported.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
