---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
671f84cd-d69f-4f8e-941f-79960ae2c907
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 500c9e7c-aa2d-479b-a3bd-5b3c39388a0c
controller          : [921308dc-111b-4c11-bff4-ee2c1aac89fd]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [8ebbac8c-0c59-4a42-a367-c24f0c4a25a4, cdbe6a3b-ef5d-4b5a-94a5-04ee2936ee77, cebbe07a-274c-4350-96ff-a31e585840d8]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 921308dc-111b-4c11-bff4-ee2c1aac89fd
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=356, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8ebbac8c-0c59-4a42-a367-c24f0c4a25a4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [75603443-f230-48a1-ba5c-7684a539b746]
name                : br0

_uuid               : cebbe07a-274c-4350-96ff-a31e585840d8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bd7d7eb6-f3ad-401d-89ed-418e43f206d0]
name                : eth7

_uuid               : cdbe6a3b-ef5d-4b5a-94a5-04ee2936ee77
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0cc5d857-5750-48bb-b89e-43dd658d415c]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : bd7d7eb6-f3ad-401d-89ed-418e43f206d0
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 75603443-f230-48a1-ba5c-7684a539b746
admin_state         : up
ifindex             : 52
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 0cc5d857-5750-48bb-b89e-43dd658d415c
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 631486bd29dc6cfe2dc7cf65495d308f4c7fca56
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Wed Dec 18 13:55:25 2013 -0800
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Thu Jan 23 16:08:53 2014 -0800

    netdev-dummy: Add support for active stream
    
    The dummy ports thus far only support passive connections. It can
    listen for multiple incoming connection requests but not make active
    connections. This patch adds support of active stream, so that a
    dummy port can be configured with either passive or active connections.
    
    The net result is that dummy ports can now connect to each other,
    without being patch ports. This feature will be useful in adding test
    cases of future commits.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
