---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e06fa2d6-a8c9-44b9-93c9-37682d6a081d
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
_uuid               : f2b84362-0575-4d57-a17a-2622fc8f1ef6
controller          : [0273e609-261d-436e-befe-886ba53f8965]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [9937ced1-cf54-41e6-8431-0b70cbfd7871, ba633ef9-aaa3-4296-b13e-cc49845f4eeb, e42d6c0a-27e3-48d3-9cb4-26b9d8ccd78f]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0273e609-261d-436e-befe-886ba53f8965
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=316, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ba633ef9-aaa3-4296-b13e-cc49845f4eeb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9b65c465-610e-4da1-adb3-539bd1b071e6]
name                : br0

_uuid               : 9937ced1-cf54-41e6-8431-0b70cbfd7871
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c0bdca4d-cac0-4519-a782-b840c8dbf81a]
name                : eth8

_uuid               : e42d6c0a-27e3-48d3-9cb4-26b9d8ccd78f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dedc7188-7958-42e8-8c40-f162e3d6d5d1]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : dedc7188-7958-42e8-8c40-f162e3d6d5d1
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
statistics          : {collisions=0, rx_bytes=3071060842, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72714352, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : c0bdca4d-cac0-4519-a782-b840c8dbf81a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6015970, tx_dropped=0, tx_errors=0, tx_packets=64129}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 9b65c465-610e-4da1-adb3-539bd1b071e6
admin_state         : up
duplex              : full
ifindex             : 785
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
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
commit 5794e276b48638c7e44a763481aa051111de1676
Author:     Pritesh Kothari &lt;pritesh.kothari@cisco.com&gt;
AuthorDate: Fri Mar 28 12:20:00 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Mar 28 14:40:07 2014 -0700

    sparse: workaround for a bug in sparse.
    
    sparse emits the following warning:
    lib/dpif-netdev.c:1755:15: warning: Initializer entry defined twice
    lib/dpif-netdev.c:1755:15:   also defined here
    due to a bug in sparse which doesn't like inlined functions which
    expands a #define within it. This commit removes inline to make
    sparse happy.
    
    Signed-off-by: Pritesh Kothari &lt;pritesh.kothari@cisco.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
