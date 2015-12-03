---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
188f0942-dc1f-4e10-8017-69f64255fb4a
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 3009e4c9-3c44-44ce-9457-ff26efa5aa8a
controller          : [69d7cc46-cd30-42a8-995e-3ac0aff6935c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [6ae69db9-0254-401f-90c8-66c70b9d6b39, aeb201db-e1aa-418f-b9c3-32395674d5e0, d0ef2cd2-9232-4b6e-b2c5-b2a3764e4fd6, d2ba5ade-4d76-490b-bae3-864c65e5ea3e]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 69d7cc46-cd30-42a8-995e-3ac0aff6935c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6ae69db9-0254-401f-90c8-66c70b9d6b39
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [54bfe409-c02a-4aad-be99-935774eeac66]
name                : "eth23"

_uuid               : d0ef2cd2-9232-4b6e-b2c5-b2a3764e4fd6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [396375a4-c56e-486c-a93c-84859464b6e9]
name                : "eth22"

_uuid               : d2ba5ade-4d76-490b-bae3-864c65e5ea3e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5cb2cc9e-c3fd-4d85-8d9e-683b5b523784]
name                : "eth21"

_uuid               : aeb201db-e1aa-418f-b9c3-32395674d5e0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [45022887-369a-4489-b244-7f2049e081a6]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 396375a4-c56e-486c-a93c-84859464b6e9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28803225649, tx_dropped=0, tx_errors=0, tx_packets=19221489}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 54bfe409-c02a-4aad-be99-935774eeac66
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5679474000, tx_dropped=0, tx_errors=0, tx_packets=3786316}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 5cb2cc9e-c3fd-4d85-8d9e-683b5b523784
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
statistics          : {collisions=0, rx_bytes=41342767591, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27605655, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 45022887-369a-4489-b244-7f2049e081a6
admin_state         : down
duplex              : full
ifindex             : 646
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
commit 1b43cf9e68f4dd0dab4f9d3fa9dd80aeb642c139
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Tue Dec 1 16:17:46 2015 -0800
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Thu Dec 3 09:54:37 2015 -0800

    ofproto-dpif: Validate ct action support.
    
    Disallow installing rules that execute ct&#40;&#41; if conntrack is unsupported
    in the datapath.
    
    Reported-by: Ravindra Kenchappa &lt;ravindra.kenchappa@hpe.com&gt;
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jarno@ovn.org&gt;
</pre>
