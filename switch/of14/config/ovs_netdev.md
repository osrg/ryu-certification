---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c5abed0c-36db-4d2d-8d5e-aecf4da4b1c2
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 3ac40be5-9f83-4f89-8870-af41bc18ec74
controller          : [77df70eb-c42a-42d5-a610-094153e36b75]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [4c6a793e-fa44-41b7-840d-f113195f13ac, a1f49297-7b23-4c9e-8ce8-b7d6d128bbcb, ad0dd19a-6c14-40f6-9097-d3c78388b9af, d551e59a-14da-4584-a17e-e88634e239ea]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 77df70eb-c42a-42d5-a610-094153e36b75
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="12", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d551e59a-14da-4584-a17e-e88634e239ea
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [86f7e5e0-e326-42a1-aedb-273c121b7a7c]
name                : "br0"

_uuid               : ad0dd19a-6c14-40f6-9097-d3c78388b9af
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a34b52e6-5c88-4ac2-b749-bf381e5445f2]
name                : "eth23"

_uuid               : 4c6a793e-fa44-41b7-840d-f113195f13ac
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [95babf14-04d4-4761-8b6b-6626d2b6e153]
name                : "eth22"

_uuid               : a1f49297-7b23-4c9e-8ce8-b7d6d128bbcb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [eba3957c-001b-4a84-a3d8-9a9581af9ff4]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : eba3957c-001b-4a84-a3d8-9a9581af9ff4
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
statistics          : {collisions=0, rx_bytes=47310652516, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31617784, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 86f7e5e0-e326-42a1-aedb-273c121b7a7c
admin_state         : down
duplex              : full
ifindex             : 846
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

_uuid               : 95babf14-04d4-4761-8b6b-6626d2b6e153
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31489297666, tx_dropped=0, tx_errors=0, tx_packets=21028556}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a34b52e6-5c88-4ac2-b749-bf381e5445f2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10152562500, tx_dropped=0, tx_errors=0, tx_packets=6768375}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 06d4d4b68726d9cf153577a4a2287f944276f0d7
Author:     Jarno Rajahalme &lt;jarno@ovn.org&gt;
AuthorDate: Wed Feb 17 14:08:04 2016 -0800
Commit:     Jarno Rajahalme &lt;jarno@ovn.org&gt;
CommitDate: Mon Feb 29 11:40:45 2016 -0800

    ofp: Add support for bundles extension in OpenFlow 1.3.
    
    ONF Extension 230 adds support for OpenFlow 1.4 bundles to OpenFlow
    1.3.  Supporting this allows OpenFlow 1.3 controllers to start using
    bundles.  Also the ovs-ofctl '--bundle' option can now be used with
    OpenFlow 1.3.
    
    Signed-off-by: Jarno Rajahalme &lt;jarno@ovn.org&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
