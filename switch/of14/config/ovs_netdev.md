---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
121e5ade-962b-46a7-aebb-655dfa268590
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
_uuid               : 5b5f39fa-ae14-4291-9cb5-9fae58ce8195
controller          : [3dfc88d1-88ca-411d-b2c8-5bfb62d2d43c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [387e8ca4-0dcc-4c8d-9a26-0cf5cbd6e668, 502007ec-841e-4e55-9fc4-cc181e0d3723, cd306fff-c269-4895-8ab5-5d28034dce50, f63f40fd-a327-471b-9c9d-d9bb77d334b5]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3dfc88d1-88ca-411d-b2c8-5bfb62d2d43c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 502007ec-841e-4e55-9fc4-cc181e0d3723
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [650619a6-3882-4eb2-90a1-08ce3a4d3ae2]
name                : "eth23"

_uuid               : 387e8ca4-0dcc-4c8d-9a26-0cf5cbd6e668
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d5bef223-f5d4-4ecb-a488-96e49efa3865]
name                : "eth21"

_uuid               : f63f40fd-a327-471b-9c9d-d9bb77d334b5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [37fd7dcb-fdd4-401b-a464-755904a073f9]
name                : "br0"

_uuid               : cd306fff-c269-4895-8ab5-5d28034dce50
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e35c98b7-7190-487b-a741-3cf3ed27ba3d]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 650619a6-3882-4eb2-90a1-08ce3a4d3ae2
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

_uuid               : d5bef223-f5d4-4ecb-a488-96e49efa3865
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

_uuid               : 37fd7dcb-fdd4-401b-a464-755904a073f9
admin_state         : down
duplex              : full
ifindex             : 339
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

_uuid               : e35c98b7-7190-487b-a741-3cf3ed27ba3d
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
commit cd144a41fda5372645403d5ec2ae4cd1cb695727
Author:     Justin Pettit &lt;jpettit@nicira.com&gt;
AuthorDate: Fri Aug 7 16:05:35 2015 -0700
Commit:     Justin Pettit &lt;jpettit@nicira.com&gt;
CommitDate: Mon Aug 10 11:33:29 2015 -0700

    ovn-architecture: Document the registers used for logical ports.
    
    When reviewing the OpenFlow flows generated by ovn-controller, it's nice
    to have this information.
    
    Signed-off-by: Justin Pettit &lt;jpettit@nicira.com&gt;
    Acked-by: Russell Bryant &lt;rbryant@redhat.com&gt;
</pre>
