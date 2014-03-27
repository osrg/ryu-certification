---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
371aa432-80c1-4b70-aca4-3e51ad4fee18
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
_uuid               : f1067e6a-097a-4f09-a64a-553e7744562a
controller          : [fde1e82e-d1a3-4ea2-a953-53727d7ba669]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0acbc983-a7fe-4124-86d3-a6ba069638ff, 26107c08-ce7f-4d6c-aeff-8a8fe3a4c26b, 8d03e763-5887-49a5-8708-377fc3f45974]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : fde1e82e-d1a3-4ea2-a953-53727d7ba669
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=15, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 26107c08-ce7f-4d6c-aeff-8a8fe3a4c26b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [63b2fba4-27be-4f77-89fc-9a28cbc96f77]
name                : br0

_uuid               : 0acbc983-a7fe-4124-86d3-a6ba069638ff
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3b9203c1-22f5-4259-9c26-46e2a0e7e1f2]
name                : eth7

_uuid               : 8d03e763-5887-49a5-8708-377fc3f45974
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [481d9164-ab38-462d-87db-e46efc10cc5f]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 63b2fba4-27be-4f77-89fc-9a28cbc96f77
admin_state         : up
ifindex             : 751
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

_uuid               : 481d9164-ab38-462d-87db-e46efc10cc5f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=19445, tx_dropped=0, tx_errors=0, tx_packets=208}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 3b9203c1-22f5-4259-9c26-46e2a0e7e1f2
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
statistics          : {collisions=0, rx_bytes=77916, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=798, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5a51b2cd3483c6c1719e5ef7091f558d49431351
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Tue Mar 25 15:26:23 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Tue Mar 25 15:26:23 2014 -0700

    lib/ofpbuf: Remove 'l7' pointer.
    
    Now that we don't need to parse TCP flags from the packet after
    extraction, we usually do not need the 'l7' pointer any more.  When
    needed, ofpbuf_get_tcp|udp|sctp|icmp_payload() or ofpbuf_get_l4_size()
    can be used instead.
    
    Removal of 'l7' was requested by Pravin for the DPDK datapath work, as
    it simplifies packet parsing a bit.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
