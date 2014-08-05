---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
df0e9d85-83e4-40a5-8cd3-3f70c4706dcf
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 66aa00dd-035c-466b-b9aa-1eb19145e856
controller          : [0eca896c-6bd1-49e7-b2b1-0cc58f07875c]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [133e25e7-2f1a-491d-855c-fbd77c48c406, 50008aea-fadd-4bd5-be12-2b8f86bf55ce, 94110c24-c65b-48d4-9bee-f766413039ee, d9b5378b-0cf0-4487-8ce6-27c333940099]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0eca896c-6bd1-49e7-b2b1-0cc58f07875c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=737, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 94110c24-c65b-48d4-9bee-f766413039ee
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8314588e-4590-4313-b712-15a141fa4fe2]
name                : eth22

_uuid               : 50008aea-fadd-4bd5-be12-2b8f86bf55ce
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [62fee147-8ac1-4376-a900-c436c2df3c37]
name                : br0

_uuid               : d9b5378b-0cf0-4487-8ce6-27c333940099
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d0eb1a76-86a3-47da-8029-1edd65ffa250]
name                : eth21

_uuid               : 133e25e7-2f1a-491d-855c-fbd77c48c406
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a2c8f3b8-3802-4527-8340-3eb4f05cff03]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a2c8f3b8-3802-4527-8340-3eb4f05cff03
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2300317500, tx_dropped=0, tx_errors=0, tx_packets=1533545}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8314588e-4590-4313-b712-15a141fa4fe2
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1065638852, tx_dropped=0, tx_errors=0, tx_packets=49397970}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d0eb1a76-86a3-47da-8029-1edd65ffa250
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=1606530371, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=84132998, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 62fee147-8ac1-4376-a900-c436c2df3c37
admin_state         : down
ifindex             : 69
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6ebad850175a9891b27562ec4d8958aa478fdcd9
Author:     Justin Pettit &lt;jpettit@nicira.com&gt;
AuthorDate: Mon Aug 4 16:00:40 2014 -0700
Commit:     Justin Pettit &lt;jpettit@nicira.com&gt;
CommitDate: Tue Aug 5 14:48:42 2014 -0700

    datapath: Correct comment about 'tun_info' member in ovs_skb_cb.
    
    Signed-off-by: Justin Pettit &lt;jpettit@nicira.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
