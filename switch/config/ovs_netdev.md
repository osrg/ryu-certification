---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6eee4a4f-72fc-41d4-afec-bd25735b1549
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : aae98ee4-5c62-471e-b835-4b76b58b269a
controller          : [9874a01d-4d42-4420-82a5-648e2d855de3]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [7c50d6e7-2846-4414-b223-f9e0aa78ee56, 9e735f40-93c3-4181-8c39-ceea9a981cf4, fddb3036-0c2e-4290-bc47-55e16c2c25e1]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9874a01d-4d42-4420-82a5-648e2d855de3
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=301, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9e735f40-93c3-4181-8c39-ceea9a981cf4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b3916dc1-f723-4241-973d-f64c3b5f09ef]
name                : br0

_uuid               : fddb3036-0c2e-4290-bc47-55e16c2c25e1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4dd54222-92cb-46d8-97e1-f9f0a04a7fef]
name                : eth8

_uuid               : 7c50d6e7-2846-4414-b223-f9e0aa78ee56
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2532f35a-ffb4-48cd-969c-20bba269d8da]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b3916dc1-f723-4241-973d-f64c3b5f09ef
admin_state         : up
duplex              : full
ifindex             : 57
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

_uuid               : 4dd54222-92cb-46d8-97e1-f9f0a04a7fef
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=306216, tx_dropped=0, tx_errors=0, tx_packets=3300}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 2532f35a-ffb4-48cd-969c-20bba269d8da
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
statistics          : {collisions=0, rx_bytes=978975, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=9900, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit db1fc2103d73ae0451f569200e70e808a7d7d79f
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Mon Jan 13 13:50:22 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Jan 13 13:50:45 2014 -0800

    netlink: Update comment for nl_dump_start().
    
    The function comment still referred to a 'msg' variable, which has been
    renamed.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    [blp@nicira.com did further proofreading]
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
