---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1674c836-f501-4da2-8d8c-e92b93c56caa
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 593aecbb-280b-4e32-b906-80821862753a
controller          : [0ed42074-f102-421a-95ee-93cc1f3145f8]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0e1a7088-91d6-46b6-a5fd-fe9fbe41c56a, 5b7412d5-67c1-470d-b1c0-81ceb9c4219f, 74bf745f-ee15-4d9a-8326-b98d9c4176da, a725eacb-8c01-4f06-a65b-52c90f157ed7]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0ed42074-f102-421a-95ee-93cc1f3145f8
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="652", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0e1a7088-91d6-46b6-a5fd-fe9fbe41c56a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [42a47f2c-0401-419a-ba3d-fb32e8f29eb2]
name                : "eth21"

_uuid               : 5b7412d5-67c1-470d-b1c0-81ceb9c4219f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b1581d20-6aa1-4813-92fa-9f2eede81154]
name                : "eth22"

_uuid               : 74bf745f-ee15-4d9a-8326-b98d9c4176da
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [13964abc-d907-4bf5-acee-74dc51dc2793]
name                : "eth23"

_uuid               : a725eacb-8c01-4f06-a65b-52c90f157ed7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ae95a21f-27a7-464a-a409-7376a29d3319]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b1581d20-6aa1-4813-92fa-9f2eede81154
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=631047262007, tx_dropped=0, tx_errors=0, tx_packets=420867190}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 42a47f2c-0401-419a-ba3d-fb32e8f29eb2
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=1233596055361, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=822780601, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 13964abc-d907-4bf5-acee-74dc51dc2793
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=42423556500, tx_dropped=0, tx_errors=0, tx_packets=28282371}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ae95a21f-27a7-464a-a409-7376a29d3319
admin_state         : down
duplex              : full
ifindex             : 929
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 966904d27f15f0c93499d79cb8bd726750369831
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Apr 16 14:38:36 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Apr 21 11:45:00 2015 -0700

    netdev-dummy: Fix null pointer deref in dummy_packet_conn_set_config&#40;&#41;.
    
    This would trigger if someone tried to switch a dummy device between
    active and passive connections.  It's not very important because dummy
    devices are only enabled during testing.
    
    Found by LLVM scan-build.
    
    Reported-by: Kevin Lo &lt;kevlo@FreeBSD.org&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
