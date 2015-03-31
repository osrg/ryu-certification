---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
40dfe77b-f346-4a7b-862f-91ed74aa0fbf
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
_uuid               : d98d9167-0aab-498e-b622-bafdaa73bb19
controller          : [9ade8b04-2e25-4e18-833a-d7fd6e2ffc81]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [6d85b5a2-55f2-4e27-a4ca-75931201f720, c76bed6e-8212-4cfc-b1a1-510db878785e, c890cfb6-e92a-4e7b-acc0-8fc1b0f5ce45, f8f0affc-666a-406d-87fe-686d44071ff0]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9ade8b04-2e25-4e18-833a-d7fd6e2ffc81
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="652", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f8f0affc-666a-406d-87fe-686d44071ff0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8f33c856-cbb1-4d24-a21c-1fba6beafcbe]
name                : "br0"

_uuid               : c890cfb6-e92a-4e7b-acc0-8fc1b0f5ce45
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [adfafe28-80ac-4f20-9348-35d5ac4c8cca]
name                : "eth21"

_uuid               : 6d85b5a2-55f2-4e27-a4ca-75931201f720
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8db10588-70cf-479a-a2a8-0ad4380c7578]
name                : "eth23"

_uuid               : c76bed6e-8212-4cfc-b1a1-510db878785e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [196af267-9603-4ae2-aa15-039877634379]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : adfafe28-80ac-4f20-9348-35d5ac4c8cca
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
statistics          : {collisions=0, rx_bytes=1205104068185, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=803752904, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 8db10588-70cf-479a-a2a8-0ad4380c7578
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=38237328000, tx_dropped=0, tx_errors=0, tx_packets=25491552}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 8f33c856-cbb1-4d24-a21c-1fba6beafcbe
admin_state         : down
duplex              : full
ifindex             : 833
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

_uuid               : 196af267-9603-4ae2-aa15-039877634379
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=610866165411, tx_dropped=0, tx_errors=0, tx_packets=407397528}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 4adb03cb6e62d938b586e68aae7af06587e58f49
Author:     Thomas Graf &lt;tgraf@noironetworks.com&gt;
AuthorDate: Mon Mar 30 12:21:09 2015 +0200
Commit:     Thomas Graf &lt;tgraf@noironetworks.com&gt;
CommitDate: Tue Mar 31 01:19:06 2015 +0200

    datapath: Use alternate name for udp_sock_create&#40;&#41; backport
    
    Account for kernels which provide udp_sock_create&#40;&#41; in an
    insufficient version.
    
    Avoids the following error when inserting openvswitch.ko on
    respective kernels:
    
    openvswitch: exports duplicate symbol udp_sock_create &#40;owned by udp_tunnel&#41;
    
    Fixes: eb6eebd28 &#40;&quot;datapath: Account for &quot;udp: Add udp_sock_create for UDP tunnels to open listener socket&quot;&#41;
    Signed-off-by: Thomas Graf &lt;tgraf@noironetworks.com&gt;
    Cc: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
