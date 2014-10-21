---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b306c4e7-e8f0-4e18-95ab-db0b1396f0d3
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
_uuid               : 581ff722-62ae-41b7-948f-fb343dae6d7c
controller          : [d8e9c902-0634-4a2d-844f-bd08aba9007a]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4b83bc6b-d922-40d9-b2ac-1c07e6bd8932, 709fd162-73d1-42c2-a93f-a200047503d5, 7eb6fafb-72d3-44ac-8746-0c005c04c8ed, 9a49a155-4214-4694-9740-61755401d2d3]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d8e9c902-0634-4a2d-844f-bd08aba9007a
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=682, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9a49a155-4214-4694-9740-61755401d2d3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e2020884-6194-4dc6-9a49-3da70f50dbfe]
name                : eth21

_uuid               : 709fd162-73d1-42c2-a93f-a200047503d5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ea0291ec-dcf4-4dc2-be36-5080fb27d54d]
name                : br0

_uuid               : 4b83bc6b-d922-40d9-b2ac-1c07e6bd8932
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b3023e2b-546d-4a07-8699-592dd8025c6c]
name                : eth23

_uuid               : 7eb6fafb-72d3-44ac-8746-0c005c04c8ed
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a5b3f4b8-35c6-4986-a3f6-51e06e0e11bb]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e2020884-6194-4dc6-9a49-3da70f50dbfe
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
statistics          : {collisions=0, rx_bytes=1900378745, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=170294424, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ea0291ec-dcf4-4dc2-be36-5080fb27d54d
admin_state         : down
duplex              : full
ifindex             : 269
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : a5b3f4b8-35c6-4986-a3f6-51e06e0e11bb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2308602392, tx_dropped=0, tx_errors=0, tx_packets=104659759}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b3023e2b-546d-4a07-8699-592dd8025c6c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3300421408, tx_dropped=0, tx_errors=0, tx_packets=7926904}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 72d52166328f52c301099efc57902c5c3c73ac68
Author:     Madhu Challa &lt;challa@noironetworks.com&gt;
AuthorDate: Sat Oct 18 13:18:01 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Oct 21 08:24:35 2014 -0700

    dpif: Fix crash in format_odp_actions&#40;&#41; due to NULL actions.
    
    When flow_get fails &#40;in this case flow does not exist&#41; simply log
    the key part of the get and erase the rest of the flow because it
    is invalid.
    
    Verified the fix by doing ovs-ofctl del-flows when traffic is running.
    
    2014-10-18T20:12:13.785Z|00011|dpif&#40;revalidator20&#41;|WARN|system@ovs-system: failed to flow_get &#40;No such file or directory&#41; dp_hash&#40;0&#41;,recirc_id&#40;0&#41;,skb_priority&#40;0&#41;,in_port&#40;2&#41;,skb_mark&#40;0&#41;,eth&#40;src=00:13:72:0b:52:fa,dst=00:14:72:0b:52:fa&#41;,eth_type&#40;0x0800&#41;,ipv4&#40;src=10.0.0.164,dst=11.0.0.164,proto=6,tos=0,ttl=4,frag=no&#41;,tcp&#40;src=1651,dst=6095&#41;,tcp_flags&#40;ack&#41;, packets:0, bytes:0, used:never
    
    Signed-off-by: Madhu Challa &lt;challa@noironetworks.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
