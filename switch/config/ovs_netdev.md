---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c732f8bc-f0e2-4042-9df4-f88dc0ef2cae
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
_uuid               : 525d83d1-3ef8-40aa-ac41-58e11f29c55f
controller          : [91cc35c3-0c31-4b1f-ac5f-b479a8d4e0eb]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1ffaa809-fff9-484f-bd71-98f80b90b3a0, 86d4d1e8-f525-4973-ac33-8b72ad9b324e, e846b898-2b85-4c61-b062-385224f09a3e]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 91cc35c3-0c31-4b1f-ac5f-b479a8d4e0eb
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=317, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e846b898-2b85-4c61-b062-385224f09a3e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c19e4407-67fa-49c8-b22a-a201aaa6789c]
name                : eth7

_uuid               : 86d4d1e8-f525-4973-ac33-8b72ad9b324e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a9e7a7dc-38fa-4628-a97b-d1d45606f849]
name                : eth8

_uuid               : 1ffaa809-fff9-484f-bd71-98f80b90b3a0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9e9d80ee-6b26-4866-924e-0e9d1a113e5f]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a9e7a7dc-38fa-4628-a97b-d1d45606f849
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5510550, tx_dropped=0, tx_errors=0, tx_packets=58747}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 9e9d80ee-6b26-4866-924e-0e9d1a113e5f
admin_state         : up
duplex              : full
ifindex             : 730
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

_uuid               : c19e4407-67fa-49c8-b22a-a201aaa6789c
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
statistics          : {collisions=0, rx_bytes=3069358504, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72697084, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
