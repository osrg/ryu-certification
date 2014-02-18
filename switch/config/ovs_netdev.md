---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a2ecede2-4f4c-42d7-840e-cf240d3c5765
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
_uuid               : 3031debe-19ac-45b3-853f-f40c1d228cd1
controller          : [141704c8-414e-4346-98ea-d6bf7951ed07]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1bce41b0-9453-4cda-ba83-d5ca8436950a, 923d7094-da0a-433a-a71d-354334a5ca30, b4b422bd-84f3-40e3-88c0-fa82f31ee524]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 141704c8-414e-4346-98ea-d6bf7951ed07
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=301, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1bce41b0-9453-4cda-ba83-d5ca8436950a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1e901a3e-e6ce-4cd7-81a5-29813f07f4f9]
name                : eth8

_uuid               : 923d7094-da0a-433a-a71d-354334a5ca30
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [501b6b39-ee75-48b2-95bb-646d91c82cad]
name                : eth7

_uuid               : b4b422bd-84f3-40e3-88c0-fa82f31ee524
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e2ca3846-0d8b-435a-8fba-b055587531bd]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 501b6b39-ee75-48b2-95bb-646d91c82cad
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
statistics          : {collisions=0, rx_bytes=3058008556, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72581947, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : e2ca3846-0d8b-435a-8fba-b055587531bd
admin_state         : up
duplex              : full
ifindex             : 268
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

_uuid               : 1e901a3e-e6ce-4cd7-81a5-29813f07f4f9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2154466, tx_dropped=0, tx_errors=0, tx_packets=23008}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9ac56358dec1a5aa7f4275a42971f55fad1f7f35
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Tue Feb 18 09:07:03 2014 -0800
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Tue Feb 18 09:56:55 2014 -0800

    datapath: Per NUMA node flow stats.
    
    Keep kernel flow stats for each NUMA node rather than each (logical)
    CPU.  This avoids using the per-CPU allocator and removes most of the
    kernel-side OVS locking overhead otherwise on the top of perf reports
    and allows OVS to scale better with higher number of threads.
    
    With 9 handlers and 4 revalidators netperf TCP_CRR test flow setup
    rate doubles on a server with two hyper-threaded physical CPUs (16
    logical cores each) compared to the current OVS master.  Tested with
    non-trivial flow table with a TCP port match rule forcing all new
    connections with unique port numbers to OVS userspace.  The IP
    addresses are still wildcarded, so the kernel flows are not considered
    as exact match 5-tuple flows.  This type of flows can be expected to
    appear in large numbers as the result of more effective wildcarding
    made possible by improvements in OVS userspace flow classifier.
    
    Perf results for this test (master):
    
    Events: 305K cycles
    +   8.43%     ovs-vswitchd  [kernel.kallsyms]   [k] mutex_spin_on_owner
    +   5.64%     ovs-vswitchd  [kernel.kallsyms]   [k] __ticket_spin_lock
    +   4.75%     ovs-vswitchd  ovs-vswitchd        [.] find_match_wc
    +   3.32%     ovs-vswitchd  libpthread-2.15.so  [.] pthread_mutex_lock
    +   2.61%     ovs-vswitchd  [kernel.kallsyms]   [k] pcpu_alloc_area
    +   2.19%     ovs-vswitchd  ovs-vswitchd        [.] flow_hash_in_minimask_range
    +   2.03%          swapper  [kernel.kallsyms]   [k] intel_idle
    +   1.84%     ovs-vswitchd  libpthread-2.15.so  [.] pthread_mutex_unlock
    +   1.64%     ovs-vswitchd  ovs-vswitchd        [.] classifier_lookup
    +   1.58%     ovs-vswitchd  libc-2.15.so        [.] 0x7f4e6
    +   1.07%     ovs-vswitchd  [kernel.kallsyms]   [k] memset
    +   1.03%          netperf  [kernel.kallsyms]   [k] __ticket_spin_lock
    +   0.92%          swapper  [kernel.kallsyms]   [k] __ticket_spin_lock
    ...
    
    And after this patch:
    
    Events: 356K cycles
    +   6.85%     ovs-vswitchd  ovs-vswitchd        [.] find_match_wc
    +   4.63%     ovs-vswitchd  libpthread-2.15.so  [.] pthread_mutex_lock
    +   3.06%     ovs-vswitchd  [kernel.kallsyms]   [k] __ticket_spin_lock
    +   2.81%     ovs-vswitchd  ovs-vswitchd        [.] flow_hash_in_minimask_range
    +   2.51%     ovs-vswitchd  libpthread-2.15.so  [.] pthread_mutex_unlock
    +   2.27%     ovs-vswitchd  ovs-vswitchd        [.] classifier_lookup
    +   1.84%     ovs-vswitchd  libc-2.15.so        [.] 0x15d30f
    +   1.74%     ovs-vswitchd  [kernel.kallsyms]   [k] mutex_spin_on_owner
    +   1.47%          swapper  [kernel.kallsyms]   [k] intel_idle
    +   1.34%     ovs-vswitchd  ovs-vswitchd        [.] flow_hash_in_minimask
    +   1.33%     ovs-vswitchd  ovs-vswitchd        [.] rule_actions_unref
    +   1.16%     ovs-vswitchd  ovs-vswitchd        [.] hindex_node_with_hash
    +   1.16%     ovs-vswitchd  ovs-vswitchd        [.] do_xlate_actions
    +   1.09%     ovs-vswitchd  ovs-vswitchd        [.] ofproto_rule_ref
    +   1.01%          netperf  [kernel.kallsyms]   [k] __ticket_spin_lock
    ...
    
    There is a small increase in kernel spinlock overhead due to the same
    spinlock being shared between multiple cores of the same physical CPU,
    but that is barely visible in the netperf TCP_CRR test performance
    (maybe ~1% performance drop, hard to tell exactly due to variance in
    the test results), when testing for kernel module throughput (with no
    userspace activity, handful of kernel flows).
    
    On flow setup, a single stats instance is allocated (for the NUMA node
    0).  As CPUs from multiple NUMA nodes start updating stats, new
    NUMA-node specific stats instances are allocated.  This allocation on
    the packet processing code path is made to never block or look for
    emergency memory pools, minimizing the allocation latency.  If the
    allocation fails, the existing preallocated stats instance is used.
    Also, if only CPUs from one NUMA-node are updating the preallocated
    stats instance, no additional stats instances are allocated.  This
    eliminates the need to pre-allocate stats instances that will not be
    used, also relieving the stats reader from the burden of reading stats
    that are never used.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
