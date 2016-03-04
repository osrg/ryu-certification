---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fed0f6a4-9a94-4622-9031-877560115c18
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 68b90780-6b91-42cc-9758-92d0d3880f5d
controller          : [587cf4f0-72ec-4be1-ab6f-98b254f67d71]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1728bd9d-2d85-44e2-b397-de41c437b69a, 377bb53f-e449-46cc-9508-4cce0ad7789c, c176806a-7203-44cc-84fb-c535e8956632, d971775b-2f27-4c52-b352-241580f140af]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 587cf4f0-72ec-4be1-ab6f-98b254f67d71
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="12", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1728bd9d-2d85-44e2-b397-de41c437b69a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bb45c0cb-63dd-4d2d-8748-5005df5bb27a]
name                : "eth22"

_uuid               : c176806a-7203-44cc-84fb-c535e8956632
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c9ab8023-d353-47f1-bbb1-aa4618211ccb]
name                : "eth23"

_uuid               : d971775b-2f27-4c52-b352-241580f140af
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [79202e9f-afd4-453e-a933-fe40f19fd536]
name                : "br0"

_uuid               : 377bb53f-e449-46cc-9508-4cce0ad7789c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2cf54abd-06f2-42db-be66-b5ae35c24c19]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2cf54abd-06f2-42db-be66-b5ae35c24c19
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
statistics          : {collisions=0, rx_bytes=47661704689, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31853792, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c9ab8023-d353-47f1-bbb1-aa4618211ccb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10415680500, tx_dropped=0, tx_errors=0, tx_packets=6943787}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : bb45c0cb-63dd-4d2d-8748-5005df5bb27a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31647305815, tx_dropped=0, tx_errors=0, tx_packets=21134857}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 79202e9f-afd4-453e-a933-fe40f19fd536
admin_state         : down
duplex              : full
ifindex             : 858
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
commit c26d70a2452ad0d7a13b72c94641d08001283119
Author:     Pravin B Shelar &lt;pshelar@ovn.org&gt;
AuthorDate: Thu Mar 3 16:15:40 2016 -0800
Commit:     Pravin B Shelar &lt;pshelar@ovn.org&gt;
CommitDate: Thu Mar 3 16:15:40 2016 -0800

    datapath: STT: Fix checksum handling.
    
    On packet receive STT verifies the checksum if not done in
    hardware. But IP and TCP were pulled before the verification
    step. The verification expect to see packet with TCP header.
    This causes STT to drop packet in certain cases.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@ovn.org&gt;
    Acked-by: Joe Stringer &lt;joe@ovn.org&gt;
</pre>
