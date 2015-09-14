---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c15393dd-f51c-4c9f-8b16-0420b5c5c822
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 11f92ffe-bed1-42fc-b8d0-c014fb47a446
controller          : [b08151f2-802a-440b-b2a2-77fc860a05bd]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [290f5017-a528-47a0-bb4c-232520d16d76, c222812d-d780-4e62-a7bf-81b3c5f1c7f1, f6101c60-2b68-45c7-b1e2-de84cad6435b, fa2f22f0-5217-4bea-b12f-c212263b104d]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b08151f2-802a-440b-b2a2-77fc860a05bd
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : fa2f22f0-5217-4bea-b12f-c212263b104d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [87975d49-b5c1-4c75-a5d8-054ec554ad6b]
name                : "eth22"

_uuid               : f6101c60-2b68-45c7-b1e2-de84cad6435b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6cdc7771-d044-4c08-a6d9-5ced0c354f82]
name                : "br0"

_uuid               : c222812d-d780-4e62-a7bf-81b3c5f1c7f1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [803fcf40-e07a-4c58-974c-21c6c9a8e974]
name                : "eth21"

_uuid               : 290f5017-a528-47a0-bb4c-232520d16d76
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f0a91187-bdeb-4dd0-a750-72da2aa7fab5]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 803fcf40-e07a-4c58-974c-21c6c9a8e974
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

_uuid               : 87975d49-b5c1-4c75-a5d8-054ec554ad6b
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

_uuid               : 6cdc7771-d044-4c08-a6d9-5ced0c354f82
admin_state         : down
duplex              : full
ifindex             : 461
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

_uuid               : f0a91187-bdeb-4dd0-a750-72da2aa7fab5
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
