---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a3956d5e-fa8c-478a-a745-31a167999696
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 22bd27db-1ab9-45a3-8b66-44d690b8831b
controller          : [be665c9c-3227-4864-b265-db8463184909]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [64ffe079-5c7b-4226-bd41-7111000f9e07, 99174bce-d14d-453a-9ade-0fc4d3cc4b8b, a2a1c0c9-0d20-4fa2-a875-0f7ac91f215a, dc5e6b0c-43ef-42e7-a5b5-f5e9d26226f8]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : be665c9c-3227-4864-b265-db8463184909
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="12", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : dc5e6b0c-43ef-42e7-a5b5-f5e9d26226f8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b0b4e7c8-7c62-4441-b4d9-c6a19b751ae8]
name                : "br0"

_uuid               : a2a1c0c9-0d20-4fa2-a875-0f7ac91f215a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7709050d-d171-44ad-b13e-5fbbb436520f]
name                : "eth23"

_uuid               : 64ffe079-5c7b-4226-bd41-7111000f9e07
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4f0bb7dd-d4cd-4625-841a-90fb8672be83]
name                : "eth21"

_uuid               : 99174bce-d14d-453a-9ade-0fc4d3cc4b8b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ce032788-6623-408a-b9cd-ef0e044bc5f8]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ce032788-6623-408a-b9cd-ef0e044bc5f8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30751887804, tx_dropped=0, tx_errors=0, tx_packets=20532459}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b0b4e7c8-7c62-4441-b4d9-c6a19b751ae8
admin_state         : down
duplex              : full
ifindex             : 790
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

_uuid               : 7709050d-d171-44ad-b13e-5fbbb436520f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=8924755500, tx_dropped=0, tx_errors=0, tx_packets=5949837}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 4f0bb7dd-d4cd-4625-841a-90fb8672be83
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
statistics          : {collisions=0, rx_bytes=45672444542, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30516437, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 45c4387b2d8d21d09c9ee6b73df5664bfee048a8
Author:     William Tu &lt;u9012063@gmail.com&gt;
AuthorDate: Thu Feb 11 09:45:08 2016 -0800
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Thu Feb 11 15:29:26 2016 -0500

    expr: Fix memory leak reported by valgrind.
    
    Testcase 1728: ovn -- 5-term mixed expression normalization.
        expr_clone_cmp &#40;expr.c:1259&#41;
        expr_clone &#40;expr.c:1284&#41;
        expr_clone_andor &#40;expr.c:1271&#41;
        expr_clone &#40;expr.c:1288&#41;
        expr_normalize_and &#40;expr.c:2137&#41;
        test_tree_shape_exhaustively &#40;test-ovn.c:926&#41;
    
    Signed-off-by: William Tu &lt;u9012063@gmail.com&gt;
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    Co-authored-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
</pre>
