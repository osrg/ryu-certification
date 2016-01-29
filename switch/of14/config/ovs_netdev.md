---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7b9c45e6-a457-4d2e-8920-2b69d5e602a7
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
_uuid               : a0cb2049-a2cc-4b13-8f9b-c34078ffc1c3
controller          : [b8b9900b-feb6-426f-ab6e-55cde2577f52]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [01cbc46d-b797-4aef-b200-fe52c0a9f642, 0e14a3ee-4cae-4b39-8fa2-5386c398b427, 22408ecd-8f4e-479e-b13c-ac269251a875, 84e84fd2-4b44-4366-ae1c-3b536d32ea0c]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b8b9900b-feb6-426f-ab6e-55cde2577f52
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 01cbc46d-b797-4aef-b200-fe52c0a9f642
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1d844551-ad1d-4092-8eda-3dd28cb27e0f]
name                : "eth21"

_uuid               : 22408ecd-8f4e-479e-b13c-ac269251a875
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c8e9bcbd-db74-4607-b921-aa2a6b524882]
name                : "eth23"

_uuid               : 0e14a3ee-4cae-4b39-8fa2-5386c398b427
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [066310c0-d7c9-4ff7-92b5-ebe43ef2e77c]
name                : "eth22"

_uuid               : 84e84fd2-4b44-4366-ae1c-3b536d32ea0c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5d0a54be-2fe9-4397-9439-488990865b14]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 066310c0-d7c9-4ff7-92b5-ebe43ef2e77c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30172532591, tx_dropped=0, tx_errors=0, tx_packets=20142694}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1d844551-ad1d-4092-8eda-3dd28cb27e0f
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
statistics          : {collisions=0, rx_bytes=44385285741, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29651096, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c8e9bcbd-db74-4607-b921-aa2a6b524882
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7960014000, tx_dropped=0, tx_errors=0, tx_packets=5306676}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 5d0a54be-2fe9-4397-9439-488990865b14
admin_state         : down
duplex              : full
ifindex             : 746
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
commit bf1f0d35ceb9ab8112b8ce3e4fa436f92bdb6410
Author:     Joe Stringer &lt;joe@ovn.org&gt;
AuthorDate: Wed Jan 27 00:49:36 2016 +0000
Commit:     Joe Stringer &lt;joe@ovn.org&gt;
CommitDate: Fri Jan 29 10:14:53 2016 -0800

    datapath: Fix IPv6 fragment expiry crash.
    
    Prior to a series of commits in 3.17 like the following, the model
    used to manage and expire fragments was different. We already backport
    several of these functions &#40;See datapath/compat/inet_fragment.c&#41; to do
    things like allocate/evict/destroy frags and frag queues. In the IPv4
    code, we use these. In most of the IPv6 cases, we already reuse these
    also. However, for timed frag expiration we instead call the upstream
    version of the function, which proceeds to use the upstream versions
    of the functions we backport in inet_fragment.c. There can be some
    discrepancy between the offsets used in these upstream versions vs. the
    backport versions, so if you mix/match them then it leads to invalid
    dereferences.
    
    b13d3cbfb8e8 &#40;&quot;inet: frag: move eviction of queues to work queue&quot;&#41;
    ab1c724f6330 &#40;&quot;inet: frag: use seqlock for hash rebuild&quot;&#41;
    
    Fixes the following kernel oops on kernels &lt; 3.17 when IPv6 fragments
    are expired without reassembling the frame.
    
    BUG: unable to handle kernel paging request at 00000006845d69a8
    IP: [&lt;ffffffff8172c09e&gt;] _raw_spin_lock+0xe/0x50
    ...
    Call Trace:
     &lt;IRQ&gt;
     [&lt;ffffffff816a32d3&gt;] inet_frag_kill+0x63/0x100
     [&lt;ffffffff816ead93&gt;] ip6_expire_frag_queue+0x63/0x110
     [&lt;ffffffffa01130e6&gt;] nf_ct_frag6_expire+0x26/0x30 [openvswitch]
     [&lt;ffffffff810744f6&gt;] call_timer_fn+0x36/0x100
     [&lt;ffffffffa01130c0&gt;] ? nf_ct_net_init+0x20/0x20 [openvswitch]
     [&lt;ffffffff8107548f&gt;] run_timer_softirq+0x1ef/0x2f0
     [&lt;ffffffff8106cccc&gt;] __do_softirq+0xec/0x2c0
     [&lt;ffffffff8106d215&gt;] irq_exit+0x105/0x110
     [&lt;ffffffff81737095&gt;] smp_apic_timer_interrupt+0x45/0x60
     [&lt;ffffffff81735a1d&gt;] apic_timer_interrupt+0x6d/0x80
     &lt;EOI&gt;
     [&lt;ffffffff8104f596&gt;] ? native_safe_halt+0x6/0x10
     [&lt;ffffffff8101cb2f&gt;] default_idle+0x1f/0xc0
     [&lt;ffffffff8101d406&gt;] arch_cpu_idle+0x26/0x30
     [&lt;ffffffff810bf3a5&gt;] cpu_startup_entry+0xc5/0x290
     [&lt;ffffffff817122e7&gt;] rest_init+0x77/0x80
     [&lt;ffffffff81d34f70&gt;] start_kernel+0x438/0x443
    
    Signed-off-by: Joe Stringer &lt;joe@ovn.org&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@ovn.org&gt;
</pre>
