---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
42181c0c-8173-46f9-9d8a-1158a50a0822
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 4c481e2b-c421-4912-be59-9b074f425002
controller          : [598e69ae-2526-4aab-8e62-26acc942f64c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5e3babb0-4032-4e49-a120-cb28db9a95f6, 8a0e4b98-7c38-48a0-81ae-32d2c1610868, fe8b16d2-f072-4565-9f14-4513f49d2cc5]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 598e69ae-2526-4aab-8e62-26acc942f64c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=927, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8a0e4b98-7c38-48a0-81ae-32d2c1610868
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [947b19fe-27ba-4176-a16f-26cb1babd37d]
name                : br0

_uuid               : 5e3babb0-4032-4e49-a120-cb28db9a95f6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [07a9554b-0180-4b09-8014-f9f0b587596a]
name                : eth8

_uuid               : fe8b16d2-f072-4565-9f14-4513f49d2cc5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [74d137ae-d0e7-4618-a40d-9eb3bd3eec80]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 74d137ae-d0e7-4618-a40d-9eb3bd3eec80
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
statistics          : {collisions=0, rx_bytes=3074599811, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72750281, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 947b19fe-27ba-4176-a16f-26cb1babd37d
admin_state         : down
duplex              : full
ifindex             : 932
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 07a9554b-0180-4b09-8014-f9f0b587596a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7071732, tx_dropped=0, tx_errors=0, tx_packets=75378}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 43f31ef528f5e4b4751036ce2ef90ea1334bbe3f
Author:     Wei Zhang &lt;asuka.com@163.com&gt;
AuthorDate: Sat Apr 5 16:17:35 2014 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Sat Apr 5 16:18:23 2014 -0700

    datapath: supply a dummy err_handler of gre_cisco_protocol to prevent kernel crash
    
    When use gre vport, openvswitch register a gre_cisco_protocol but
    does not supply a err_handler with it. The gre_cisco_err() in
    net/ipv4/gre_demux.c expect err_handler be provided with the
    gre_cisco_protocol implementation, and call -&gt;err_handler() without
    existence check, cause the kernel crash.
    
    This patch provide a err_handler to fix this bug.
    
    Signed-off-by: Wei Zhang &lt;asuka.com@163.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
