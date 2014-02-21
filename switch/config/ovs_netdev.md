---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
5f080b9c-3ce8-419e-a576-8e835870d96b
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e933e7a6-7889-40e2-ba46-abc99dbd7ea6
controller          : [0ec83b38-a0d4-47a3-8bbb-e9fccdef842d]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [28903d16-78f9-40c6-965d-2983a124f35e, b4224c5e-5b8b-41a2-a427-88e0c329eef7, d65cc7e1-0b34-416c-a885-894b658a1444]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0ec83b38-a0d4-47a3-8bbb-e9fccdef842d
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=397, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d65cc7e1-0b34-416c-a885-894b658a1444
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c2564ea8-dfd4-48d4-a085-af4c2d65c26c]
name                : br0

_uuid               : 28903d16-78f9-40c6-965d-2983a124f35e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a139ba73-d0f6-4d8d-afe6-510511c304cf]
name                : eth8

_uuid               : b4224c5e-5b8b-41a2-a427-88e0c329eef7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ecc336a6-f81e-482e-8342-7ebcb4b6a3c4]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c2564ea8-dfd4-48d4-a085-af4c2d65c26c
admin_state         : up
duplex              : full
ifindex             : 326
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

_uuid               : ecc336a6-f81e-482e-8342-7ebcb4b6a3c4
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
statistics          : {collisions=0, rx_bytes=3059484469, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72596887, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : a139ba73-d0f6-4d8d-afe6-510511c304cf
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2605424, tx_dropped=0, tx_errors=0, tx_packets=27814}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ece7040fe4c4b02c279afbb6dfc9d05687908000
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Feb 21 10:50:56 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Feb 21 10:51:21 2014 -0800

    ovs-thread: Get rid of obsolete sparse wrappers.
    
    These were useful back when we were trying to use the sparse lock balance
    annotations, but we removed those in commit 47b52c71232c0 (sparse: Remove
    support for thread-safety annotations.) and so they serve no purpose any
    longer.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
