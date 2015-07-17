---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f65470f3-cea7-4738-9296-74a04bafc612
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7a42dbad-2c12-41e1-bcc9-1f611208bf73
controller          : [d19ab94b-5632-44c4-a3f0-6a651b400aa7]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3d9f2828-8ba5-484b-8195-b9ac58fba150, 5d1e74c7-cc0c-4cc0-81b9-1f8cf2590fc8, 9787c403-3b5e-469b-9cb3-864299dcb18d, b7d9d725-c3a1-4ef9-a45b-5ad99884aaa4]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d19ab94b-5632-44c4-a3f0-6a651b400aa7
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3d9f2828-8ba5-484b-8195-b9ac58fba150
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b2ca9e63-c284-4c03-a5dc-89aa5bf685d7]
name                : "br0"

_uuid               : b7d9d725-c3a1-4ef9-a45b-5ad99884aaa4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d2607a9a-8d14-4939-b172-d5e5cfa88b03]
name                : "eth22"

_uuid               : 9787c403-3b5e-469b-9cb3-864299dcb18d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [77d4d3ce-23d0-4447-91e5-b4f57895d318]
name                : "eth23"

_uuid               : 5d1e74c7-cc0c-4cc0-81b9-1f8cf2590fc8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [56152c7c-9b5c-484d-a3e9-394abda8d2d5]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 56152c7c-9b5c-484d-a3e9-394abda8d2d5
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

_uuid               : d2607a9a-8d14-4939-b172-d5e5cfa88b03
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

_uuid               : 77d4d3ce-23d0-4447-91e5-b4f57895d318
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

_uuid               : b2ca9e63-c284-4c03-a5dc-89aa5bf685d7
admin_state         : down
duplex              : full
ifindex             : 261
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
commit 0e469d3b380cd6137d752810d070657b1eb2fed0
Author:     Neil McKee &lt;neil.mckee@inmon.com&gt;
AuthorDate: Thu Jun 11 09:43:58 2015 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Fri Jul 17 13:23:39 2015 -0700

    datapath: Include datapath actions with sampled-packet upcall to userspace.
    
    If new optional attribute OVS_USERSPACE_ATTR_ACTIONS is added to an
    OVS_ACTION_ATTR_USERSPACE action, then include the datapath actions
    in the upcall.
    
    This Directly associates the sampled packet with the path it takes
    through the virtual switch. Path information currently includes mangling,
    encapsulation and decapsulation actions for tunneling protocols GRE,
    VXLAN, Geneve, MPLS and QinQ, but this extension requires no further
    changes to accommodate datapath actions that may be added in the
    future.
    
    Adding path information enhances visibility into complex virtual
    networks.
    
    Signed-off-by: Neil McKee &lt;neil.mckee@inmon.com&gt;
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
