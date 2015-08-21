---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d58879d4-a333-48fb-8c1e-8f07472dc40d
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 67c25f56-3cb2-4600-8024-69785e2ed76a
controller          : [e790bb74-2f93-425a-94e9-d9b5a457059d]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [534f03c6-a866-47f7-b870-da4aa7c194ce, afc96222-5f0a-48d0-870c-caf7a9348454, df0cf495-88a0-4df3-8efa-0729b09ceee6, fb9912e3-0c52-4213-a783-ba78f8fbcd57]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e790bb74-2f93-425a-94e9-d9b5a457059d
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : df0cf495-88a0-4df3-8efa-0729b09ceee6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ec79eab2-78b1-4426-b0cf-c743084e0e4b]
name                : "eth22"

_uuid               : afc96222-5f0a-48d0-870c-caf7a9348454
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9e6290cc-fd92-4062-8ec8-b260650b32c4]
name                : "br0"

_uuid               : 534f03c6-a866-47f7-b870-da4aa7c194ce
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2ee1e7bc-8b06-4db4-a23d-f2facb09bfd0]
name                : "eth21"

_uuid               : fb9912e3-0c52-4213-a783-ba78f8fbcd57
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c6511cbc-6bd4-43b5-b1ae-805c42b1ebb3]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2ee1e7bc-8b06-4db4-a23d-f2facb09bfd0
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
statistics          : {collisions=0, rx_bytes=24024581534, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16026376, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9e6290cc-fd92-4062-8ec8-b260650b32c4
admin_state         : down
duplex              : full
ifindex             : 377
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

_uuid               : c6511cbc-6bd4-43b5-b1ae-805c42b1ebb3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1176922500, tx_dropped=0, tx_errors=0, tx_packets=784615}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ec79eab2-78b1-4426-b0cf-c743084e0e4b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18089315792, tx_dropped=0, tx_errors=0, tx_packets=12064077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1add079ee202918e9f6739aa02b8e8259964b346
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Fri Aug 21 12:49:46 2015 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Fri Aug 21 12:49:46 2015 -0700

    test-classifier: Add benchmark.
    
    Add a benchmark command for classifier lookup performance testing.
    
    Running the test-classifier without arguments of with &quot;--help&quot; will
    print the following usage:
    
    usage: ovstest test-classifier benchmark &lt;n_rules&gt; &lt;n_priorities&gt; &lt;n_subtables&gt; &lt;n_threads&gt; &lt;n_lookups&gt;
    
    where:
    
    &lt;n_rules&gt;      - The number of rules to install for lookups.  More rules
                     makes misses less likely.
    &lt;n_priorities&gt; - How many different priorities to use.  Using only 1
                     priority will force lookups to continue through all
                     subtables.
    &lt;n_subtables&gt;  - Number of subtables to use.  Normally a classifier has
                     rules with different kinds of masks, resulting in
                     multiple subtables &#40;one per mask&#41;.  However, in some
                     special cases a table may consist of only one kind of
                     rules, so there will be only one subtable.
    &lt;n_threads&gt;    - How many lookup threads to use.  Using one thread should
                     give less variance accross runs, but classifier
                     scaling can be tested with multiple threads.
    &lt;n_lookups&gt;    - How many lookups each thread should perform.
    
    
    For testing the classifier is filled with &lt;n_rules&gt; rules using
    &lt;n_subtables&gt; different mask patterns and &lt;n_priorities&gt; different
    priorities.  A random set of lookup flows are created, and &lt;n_threads&gt;
    lookup threads are spawned to perform &lt;n_lookups&gt; lookups each.  The
    count of hits and misses, as well as the overall execution time is
    reported.
    
    Example run:
    
    $ tests/ovstest test-classifier benchmark 1000 1 30 1 3800000
    
    Benchmarking with:
    1000 rules with 1 priorities in 30 tables, 1 threads doing 3800000 lookups each
    
    Without wildcards:
    
    hits: 461520, misses: 3338480
    classifier lookups:    386 ms, 9844559 lookups/sec
    
    With wildcards:
    
    hits: 461520, misses: 3338480
    classifier lookups:    866 ms, 4387990 lookups/sec
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
