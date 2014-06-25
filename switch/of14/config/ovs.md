---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
5aa36ed7-e27a-4d5d-b0e3-f45ca042669c
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 09e2dd04-6dc4-4ec1-865f-ea8f41c20b80
controller          : [ccdb055e-4cf5-4962-9d00-cad1d8686912]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2ca2d535-f65e-462d-8402-91e4117557e8, 5c759abc-140b-4c9f-8531-bcac923fd3e3, 790a80ce-9f68-4fcf-acb6-c216bcb6fba4, c72de769-232a-40eb-84de-cab0b01661ce]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ccdb055e-4cf5-4962-9d00-cad1d8686912
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=987, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5c759abc-140b-4c9f-8531-bcac923fd3e3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [882b677d-0fb8-4913-9700-661882bd7a2f]
name                : br0

_uuid               : 2ca2d535-f65e-462d-8402-91e4117557e8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [08e5221b-536b-4238-a1d6-8f15770bf6a2]
name                : eth22

_uuid               : c72de769-232a-40eb-84de-cab0b01661ce
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b8d617fa-cea3-4729-80df-330f4d857e5e]
name                : eth23

_uuid               : 790a80ce-9f68-4fcf-acb6-c216bcb6fba4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [55098c0c-081b-4e9b-880c-cc65dc0dbd2b]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 55098c0c-081b-4e9b-880c-cc65dc0dbd2b
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
statistics          : {collisions=0, rx_bytes=3337807064, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=91120733, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 882b677d-0fb8-4913-9700-661882bd7a2f
admin_state         : down
ifindex             : 690
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

_uuid               : b8d617fa-cea3-4729-80df-330f4d857e5e
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=1418183784, tx_dropped=0, tx_errors=0, tx_packets=12399386}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 08e5221b-536b-4238-a1d6-8f15770bf6a2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2179352542, tx_dropped=0, tx_errors=0, tx_packets=35863720}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e381def9712019bfb667605c1f3dba5ce2266c44
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Tue Jun 24 13:00:52 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Wed Jun 25 09:28:42 2014 -0700

    lib: Rename ofp to buf.
    
    dpif-packet contains ofpbuf which points to packet data.  Here buf
    is better name rather than ofp.
    Following patch renames all remaining instances of ofp variable.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
</pre>
