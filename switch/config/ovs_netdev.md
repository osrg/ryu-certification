---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
325c11c7-7c0a-45b0-a4a7-d75d9ce55c85
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 9c501a9c-ab75-4c5d-8843-51cea3a6574e
controller          : [6858b076-fa03-483b-a151-f89d7f6bef4d]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [17a39e2f-b297-44a6-83be-601d785cf8ad, 513447f2-ea5d-4437-967a-444f98f36563, bfd00002-3017-45d1-994d-ebafb3892b42, c4529782-1af7-4420-be99-ee2d62a9f0f3]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6858b076-fa03-483b-a151-f89d7f6bef4d
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 513447f2-ea5d-4437-967a-444f98f36563
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ec1980ca-77e1-42a7-97d4-324cdeaeda68]
name                : "eth23"

_uuid               : bfd00002-3017-45d1-994d-ebafb3892b42
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c885d6be-d0f6-4be4-b81b-31b2653b0e42]
name                : "eth22"

_uuid               : c4529782-1af7-4420-be99-ee2d62a9f0f3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6ad2080a-6e5b-43fa-b286-98ed3c32eb76]
name                : "eth21"

_uuid               : 17a39e2f-b297-44a6-83be-601d785cf8ad
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b3555669-72f7-4d47-8ad1-92aef8bd173d]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b3555669-72f7-4d47-8ad1-92aef8bd173d
admin_state         : down
duplex              : full
ifindex             : 459
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

_uuid               : c885d6be-d0f6-4be4-b81b-31b2653b0e42
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

_uuid               : ec1980ca-77e1-42a7-97d4-324cdeaeda68
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

_uuid               : 6ad2080a-6e5b-43fa-b286-98ed3c32eb76
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
commit dd693f9bf23ae1108d956c5d58a7036dcb636e19
Author:     Jiri Benc &lt;jbenc@redhat.com&gt;
AuthorDate: Thu Sep 10 06:15:32 2015 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Mon Sep 14 10:44:57 2015 -0700

    datapath: Use netlink ipv4 API to handle the ipv4 addr attributes.
    
    upstream: &#40;&quot;netlink: implement nla_put_in_addr and nla_put_in6_addr&quot;&#41;
    upstream: &#40;&quot;netlink: implement nla_get_in_addr and nla_get_in6_addr&quot;&#41;
    IP addresses are often stored in netlink attributes. Add generic functions
    to do that.
    
    Signed-off-by: Jiri Benc &lt;jbenc@redhat.com&gt;
    Signed-off-by: David S. Miller &lt;davem@davemloft.net&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
