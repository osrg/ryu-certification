---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4d940db4-b2df-4ce7-b52f-856e44b80f98
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a14546e7-2b56-4033-b37e-2c14cc4fc61f
controller          : [8842b134-fd2b-422c-bbda-b091a9a272c4]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [45c99a7f-6009-4fe8-a6a0-e778481efd07, 960cd20d-d8c3-4fca-8061-b5ee6e47793a, 9e222668-8aef-40a7-8c5f-9fc58f9a3d36, c95c38ef-68a0-450c-9100-6b5c35bca24d]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8842b134-fd2b-422c-bbda-b091a9a272c4
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="657", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9e222668-8aef-40a7-8c5f-9fc58f9a3d36
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [47b05e80-b393-470f-9f23-46fb1beb3d73]
name                : "br0"

_uuid               : 960cd20d-d8c3-4fca-8061-b5ee6e47793a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [478eff5d-e068-4276-8b5f-d608ed6d00d5]
name                : "eth22"

_uuid               : c95c38ef-68a0-450c-9100-6b5c35bca24d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [83b93773-3ef5-441b-8620-63214e0741fb]
name                : "eth23"

_uuid               : 45c99a7f-6009-4fe8-a6a0-e778481efd07
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d260808d-947e-4c0e-a19b-4ebec7b6ba18]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 47b05e80-b393-470f-9f23-46fb1beb3d73
admin_state         : down
duplex              : full
ifindex             : 830
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

_uuid               : 478eff5d-e068-4276-8b5f-d608ed6d00d5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=610729316968, tx_dropped=0, tx_errors=0, tx_packets=407305776}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d260808d-947e-4c0e-a19b-4ebec7b6ba18
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
statistics          : {collisions=0, rx_bytes=1204881949872, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=803603763, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 83b93773-3ef5-441b-8620-63214e0741fb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=38107678500, tx_dropped=0, tx_errors=0, tx_packets=25405119}
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
