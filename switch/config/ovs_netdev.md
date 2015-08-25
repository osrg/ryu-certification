---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ce331c46-ab91-4948-90a3-17a9b8769dcc
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
_uuid               : 74b9b295-87c7-44bd-8506-c1f28a510a98
controller          : [800d07ac-187d-433f-8f3c-152e048bb52e]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [27bbcdb9-cebb-406d-9424-389e2678cc4f, 44664f6a-498f-430d-99cf-2a87acc6cb97, c57b8597-ac9e-4406-8216-8a3e981133fa, db70367c-4500-43c0-9f2a-de37b8438579]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 800d07ac-187d-433f-8f3c-152e048bb52e
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : db70367c-4500-43c0-9f2a-de37b8438579
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [babefb1d-2789-4010-b6f8-0cbb56878962]
name                : "eth23"

_uuid               : 27bbcdb9-cebb-406d-9424-389e2678cc4f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9f3950b4-ab65-4566-a591-08f5b182e112]
name                : "eth21"

_uuid               : 44664f6a-498f-430d-99cf-2a87acc6cb97
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [30162e92-9dde-44e9-a58e-f718b609026b]
name                : "eth22"

_uuid               : c57b8597-ac9e-4406-8216-8a3e981133fa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [479125ad-c6ab-40e2-9617-25ff2b89c48f]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9f3950b4-ab65-4566-a591-08f5b182e112
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

_uuid               : 479125ad-c6ab-40e2-9617-25ff2b89c48f
admin_state         : down
duplex              : full
ifindex             : 387
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

_uuid               : babefb1d-2789-4010-b6f8-0cbb56878962
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

_uuid               : 30162e92-9dde-44e9-a58e-f718b609026b
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
commit c02c4967b9623dff6d2a10ac17cfa6444bddaf97
Author:     Wenyu Zhang &lt;wenyuz@vmware.com&gt;
AuthorDate: Mon Aug 24 20:56:44 2015 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Tue Aug 25 09:55:44 2015 -0700

    datapath: Make 100 percents packets sampled when sampling rate is 1.
    
    When sampling rate is 1, the sampling probability is UINT32_MAX. The packet
    should be sampled even the prandom32&#40;&#41; generate the number of UINT32_MAX.
    And none packet need be sampled when the probability is 0.
    
    Signed-off-by: Wenyu Zhang &lt;wenyuz@vmware.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Signed-off-by: David S. Miller &lt;davem@davemloft.net&gt;
    
    Upstream: e05176a3283 &#40;&quot;openvswitch: Make 100 percents packets
    sampled when sampling rate is 1.&quot;&#41;
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
