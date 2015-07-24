---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7a7e0375-3fdf-4a23-b171-a8455cc4d4bd
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
_uuid               : 492fc407-38b2-4a38-be29-f0839fc3567f
controller          : [5538929e-1d41-4f60-ab1e-4ab79e2a79c3]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0a8aa5bc-68d2-4b5b-bc67-660989b57138, 3da7db90-9979-4291-9cf3-c1da7a2b4b46, 5e0f3ba6-25c0-442e-8f8b-30caff2447d2, 9d878162-f458-4465-ad2c-2c2c8095c8bb]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5538929e-1d41-4f60-ab1e-4ab79e2a79c3
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3da7db90-9979-4291-9cf3-c1da7a2b4b46
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f1eeb737-3997-414c-9bb8-e699d6e94a7c]
name                : "eth23"

_uuid               : 0a8aa5bc-68d2-4b5b-bc67-660989b57138
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5a2cbb2f-ca38-4d68-8b8d-b9ee40a2bb82]
name                : "eth21"

_uuid               : 5e0f3ba6-25c0-442e-8f8b-30caff2447d2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a5fc7902-8c42-4aa6-915e-1ff6043c28d3]
name                : "eth22"

_uuid               : 9d878162-f458-4465-ad2c-2c2c8095c8bb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [91156b46-7dd8-48ca-9c9a-8f6a2d409171]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 91156b46-7dd8-48ca-9c9a-8f6a2d409171
admin_state         : down
duplex              : full
ifindex             : 285
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

_uuid               : a5fc7902-8c42-4aa6-915e-1ff6043c28d3
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

_uuid               : 5a2cbb2f-ca38-4d68-8b8d-b9ee40a2bb82
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

_uuid               : f1eeb737-3997-414c-9bb8-e699d6e94a7c
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ad2e649834be20dd01b1632799fe778106a96a2d
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Jul 23 16:22:39 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Jul 24 13:49:19 2015 -0700

    tunnel: Drop 'base_flow' parameter from tnl_xlate_init&#40;&#41;.
    
    At the point when tnl_xlate_init&#40;&#41; is called, all of the members that
    tnl_xlate_init&#40;&#41; examines in 'base_flow' have the same values in 'flow',
    so there's no point in passing both.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
