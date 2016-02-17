---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d6b6e027-e2f8-4313-bd3a-c58f79cae08d
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 952e4575-cdfe-45b4-a742-19dfb133619c
controller          : [f2921273-ec12-4cfa-8b22-d750b0f708a7]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [450a740a-0f08-4ba0-927a-0d8d53b275cb, 94dff123-f9da-41bc-9db3-85d3cd35d4ef, ad3ee9c1-429a-42be-819c-ba4070d82169, e4929d8a-28ba-4fcf-aedb-1ae7351a07a8]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f2921273-ec12-4cfa-8b22-d750b0f708a7
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="4", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ad3ee9c1-429a-42be-819c-ba4070d82169
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7a14270b-0ce5-487f-a0a7-a6d31657984e]
name                : "eth22"

_uuid               : e4929d8a-28ba-4fcf-aedb-1ae7351a07a8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8a5e8d25-1d03-4f40-8012-a181f4d1d544]
name                : "eth23"

_uuid               : 450a740a-0f08-4ba0-927a-0d8d53b275cb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [50f26ee1-3edf-428d-ab06-2427937a187a]
name                : "br0"

_uuid               : 94dff123-f9da-41bc-9db3-85d3cd35d4ef
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0d71b579-a4a4-4596-9c58-49828156b8f9]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 50f26ee1-3edf-428d-ab06-2427937a187a
admin_state         : down
duplex              : full
ifindex             : 802
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

_uuid               : 8a5e8d25-1d03-4f40-8012-a181f4d1d544
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9275847000, tx_dropped=0, tx_errors=0, tx_packets=6183898}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 0d71b579-a4a4-4596-9c58-49828156b8f9
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
statistics          : {collisions=0, rx_bytes=46140513090, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30831108, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7a14270b-0ce5-487f-a0a7-a6d31657984e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30962302820, tx_dropped=0, tx_errors=0, tx_packets=20674013}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 598ff4b2d09d8194a40b850b6eb110797ab4d1b2
Author:     Ben Pfaff &lt;blp@ovn.org&gt;
AuthorDate: Tue Feb 16 15:33:42 2016 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Tue Feb 16 21:11:13 2016 -0800

    openflow-common: Describe length and padding rules for OpenFlow properties.
    
    I keep having to rediscover these from the code.  This is easier.
    
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
    Acked-by: Joe Stringer &lt;joe@ovn.org&gt;
</pre>
