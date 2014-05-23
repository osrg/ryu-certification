---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
308e0b2c-ef73-4ef8-8894-4525ce113022
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : bb88fad3-56c5-4622-a9f5-80ceab23f2fb
controller          : [0f279932-e9e0-48a9-bfe3-57c2f131d0a8]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2a44dcc9-2fe3-4aaa-81dc-cf0abc6b60fb, 5fd047a2-2304-45f8-99d8-d554a1a8be20, 8e3fa259-203b-4fa2-8198-8592911f06fc, a9d886c2-0e17-4d0d-8cce-1b8be823b922]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0f279932-e9e0-48a9-bfe3-57c2f131d0a8
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=552, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2a44dcc9-2fe3-4aaa-81dc-cf0abc6b60fb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8f6859ff-5846-476f-b860-720be1ec7c88]
name                : br0

_uuid               : 8e3fa259-203b-4fa2-8198-8592911f06fc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8e8cd139-c7ba-4da5-bfeb-b0393104dd4a]
name                : eth21

_uuid               : a9d886c2-0e17-4d0d-8cce-1b8be823b922
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c049064e-8fd6-43ac-a346-8589341e3304]
name                : eth23

_uuid               : 5fd047a2-2304-45f8-99d8-d554a1a8be20
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fb83857d-3261-4f55-a130-56592e770de1]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : fb83857d-3261-4f55-a130-56592e770de1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2026490632, tx_dropped=0, tx_errors=0, tx_packets=1357625}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8e8cd139-c7ba-4da5-bfeb-b0393104dd4a
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
statistics          : {collisions=0, rx_bytes=777293936, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=3399154, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c049064e-8fd6-43ac-a346-8589341e3304
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3629622000, tx_dropped=0, tx_errors=0, tx_packets=2419748}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8f6859ff-5846-476f-b860-720be1ec7c88
admin_state         : down
duplex              : full
ifindex             : 191
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fdb1999b2bd239d3074bcae675cf18213bb250b8
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Thu May 22 09:35:36 2014 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Thu May 22 17:06:30 2014 -0700

    ofproto-dpif-xlate: Coding style fix for bucket_is_alive&#40;&#41;
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
