---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4b0471e2-4f53-47f8-a840-ef424c1f0008
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
_uuid               : 7265b066-4450-4ebc-b063-03dbed6f2ce0
controller          : [cc75a173-d761-4ade-bdeb-77399df416de]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [12b4ca0b-bd0f-4589-a059-fdf1ef40f1eb, 2e6eb827-9962-4c0e-8688-e85a1d535563, af0b3b8a-8356-4a51-bcd5-c0493109429d, ee18093a-c57d-46e5-8214-d0a605d7a8fd]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : cc75a173-d761-4ade-bdeb-77399df416de
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="757", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : af0b3b8a-8356-4a51-bcd5-c0493109429d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1694e832-449f-44fa-9fec-c3a4454c2f27]
name                : "eth22"

_uuid               : ee18093a-c57d-46e5-8214-d0a605d7a8fd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f4a96322-aaa1-406f-866e-073ea5a621bf]
name                : "eth21"

_uuid               : 2e6eb827-9962-4c0e-8688-e85a1d535563
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9787e57b-66f4-4059-a267-a8a2a6a19682]
name                : "br0"

_uuid               : 12b4ca0b-bd0f-4589-a059-fdf1ef40f1eb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6165ee19-8b41-4677-92fc-b1ed9d3d0abb]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6165ee19-8b41-4677-92fc-b1ed9d3d0abb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5328567000, tx_dropped=0, tx_errors=0, tx_packets=3552378}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f4a96322-aaa1-406f-866e-073ea5a621bf
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
statistics          : {collisions=0, rx_bytes=40874627313, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27290939, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1694e832-449f-44fa-9fec-c3a4454c2f27
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28592539306, tx_dropped=0, tx_errors=0, tx_packets=19079788}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9787e57b-66f4-4059-a267-a8a2a6a19682
admin_state         : down
duplex              : full
ifindex             : 628
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
commit 607c5e55ae403763b7c0d7df262637c53135cd76
Author:     Justin Pettit &lt;jpettit@ovn.org&gt;
AuthorDate: Fri Nov 6 13:53:34 2015 -0800
Commit:     Justin Pettit &lt;jpettit@ovn.org&gt;
CommitDate: Fri Nov 6 16:33:29 2015 -0800

    TODO.md: Remove old item.
    
    The patchwork instance has been recreated, so this doesn't point any
    place valid.
    
    Signed-off-by: Justin Pettit &lt;jpettit@ovn.org&gt;
    Acked-by: Russell Bryant &lt;rbryant@redhat.com&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
