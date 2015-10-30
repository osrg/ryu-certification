---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fe568fa8-cd05-4e8e-b38f-7141d1d3de6b
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c33c12f8-2026-40a1-a7a5-914c7d3ff8ca
controller          : [1c247c46-ee37-4dba-9bfa-7dc02da6a13a]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [67dfbbf0-6996-4487-9a6c-e2c42e4c7c82, 9107b540-1696-4a11-95a3-315463431244, a8979e89-581e-4394-bff3-1ac7fc2c1d87, ac7587a3-a8c4-4d84-b9a7-7054b4b3e730]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 1c247c46-ee37-4dba-9bfa-7dc02da6a13a
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="767", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9107b540-1696-4a11-95a3-315463431244
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d2ff7d2b-2c23-4a2b-bd12-34c253342526]
name                : "eth22"

_uuid               : 67dfbbf0-6996-4487-9a6c-e2c42e4c7c82
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6db74c5b-f101-4801-b8ef-9e57ee31bbb9]
name                : "eth23"

_uuid               : a8979e89-581e-4394-bff3-1ac7fc2c1d87
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8a475f2d-1933-43b2-99e0-6cf44bc1d0ce]
name                : "eth21"

_uuid               : ac7587a3-a8c4-4d84-b9a7-7054b4b3e730
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [30169eec-a3d5-4fb8-961e-3129619e5fd9]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 30169eec-a3d5-4fb8-961e-3129619e5fd9
admin_state         : down
duplex              : full
ifindex             : 607
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

_uuid               : 8a475f2d-1933-43b2-99e0-6cf44bc1d0ce
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
statistics          : {collisions=0, rx_bytes=40184310018, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26827075, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d2ff7d2b-2c23-4a2b-bd12-34c253342526
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28245233536, tx_dropped=0, tx_errors=0, tx_packets=18846643}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 6db74c5b-f101-4801-b8ef-9e57ee31bbb9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4847751000, tx_dropped=0, tx_errors=0, tx_packets=3231834}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e2167cb7204a94bb1530daa37c4b81661475a583
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Thu Oct 29 14:51:34 2015 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Fri Oct 30 11:13:10 2015 -0700

    test: Make test independent of the recirc_id
    
    Commit 8ae8176fd0d8ed919e3301cc961dcf02b65ff49d &#40;tests: Make test
    independent of the hash function&#41; improves the test &quot;ofprot-dpif
    - balance-tcp bonding, different recirc flow&quot; to not dependent on
    the values of dp-hash, but it still depends on the value of recirc_id,
    which can be a different value based on runs, specifically, it depends
    which one of the two bonds allocates recirc id first.
    
    Since both dp_hash and recirc_id values are runtime dependent,
    consolidate the masking scripts into ofctl_strip.
    
    Bug-report: http://openvswitch.org/pipermail/discuss/2015-October/019269.html
    Reported-by: Gerhrd Stenzel &lt;gstenzel@linux.vnet.ibm.com&gt;
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
