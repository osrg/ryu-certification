---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
5bd1260a-05e3-4946-82eb-546a19366e91
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d05903c1-49a7-408d-89a4-53af1b18a85e
controller          : [f5b8eb0a-4d59-428f-8489-ef9b3d805822]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [733fdfb7-3bf2-4f43-91b2-38ec434f9606, 814776d1-dbe9-4909-91ef-b3bccd0a09e5, 9c49403b-b977-4b63-ba2a-0ba97244e806, f3349e88-4575-4eed-b57e-769bc3866f87]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f5b8eb0a-4d59-428f-8489-ef9b3d805822
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=661, sec_since_disconnect=7, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f3349e88-4575-4eed-b57e-769bc3866f87
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8b48825e-2dc1-4a17-b1ab-313dfccce292]
name                : eth21

_uuid               : 814776d1-dbe9-4909-91ef-b3bccd0a09e5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3fd51b03-62ba-423e-bb2f-499b85521630]
name                : eth23

_uuid               : 9c49403b-b977-4b63-ba2a-0ba97244e806
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dc53cbbf-8527-4566-b7ae-9dfdd691fcf7]
name                : eth22

_uuid               : 733fdfb7-3bf2-4f43-91b2-38ec434f9606
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fac4f759-0a09-42c2-b76c-2a1c43b32074]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : fac4f759-0a09-42c2-b76c-2a1c43b32074
admin_state         : down
duplex              : full
ifindex             : 108
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 8b48825e-2dc1-4a17-b1ab-313dfccce292
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=3137696966, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=56525433, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3fd51b03-62ba-423e-bb2f-499b85521630
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4167385500, tx_dropped=0, tx_errors=0, tx_packets=2778257}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : dc53cbbf-8527-4566-b7ae-9dfdd691fcf7
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3593273226, tx_dropped=0, tx_errors=0, tx_packets=39632390}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 800711c3c2c79464d837872f681ab3d257e8fdd6
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Sun Sep 7 15:18:07 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Mon Sep 8 10:43:36 2014 -0700

    datapath: Set packet egress_tun_info.
    
    packet execute is setting egress_tun_info in skb-&gt;cb, rather
    than packet-&gt;cb. skb is netlink msg skb. This causes corruption
    in netlink skb state stored in skb-&gt;cb &#40;NETLINK_CB&#41; which
    results in following deadlock in netlink code.
    
    =============================================
    [ INFO: possible recursive locking detected ]
    3.2.62 #2
    ---------------------------------------------
    handler55/22851 is trying to acquire lock:
     &#40;genl_mutex&#41;{+.+.+.}, at: [&lt;ffffffff81471ad7&gt;] genl_lock+0x17/0x20
    
    but task is already holding lock:
     &#40;genl_mutex&#41;{+.+.+.}, at: [&lt;ffffffff81471ad7&gt;] genl_lock+0x17/0x20
    
    other info that might help us debug this:
     Possible unsafe locking scenario:
    
           CPU0
           ----
      lock&#40;genl_mutex&#41;;
      lock&#40;genl_mutex&#41;;
    
     *** DEADLOCK ***
    
     May be due to missing lock nesting notation
    
    1 lock held by handler55/22851:
     #0:  &#40;genl_mutex&#41;{+.+.+.}, at: [&lt;ffffffff81471ad7&gt;] genl_lock+0x17/0x20
    
    stack backtrace:
    Pid: 22851, comm: handler55 Tainted: G           O 3.2.62 #2
    Call Trace:
     [&lt;ffffffff81097bb2&gt;] print_deadlock_bug+0xf2/0x100
     [&lt;ffffffff81099b99&gt;] validate_chain+0x579/0x860
     [&lt;ffffffff8109a17c&gt;] __lock_acquire+0x2fc/0x4f0
     [&lt;ffffffff8109aab0&gt;] lock_acquire+0xa0/0x180
     [&lt;ffffffff81519070&gt;] __mutex_lock_common+0x60/0x420
     [&lt;ffffffff8151959a&gt;] mutex_lock_nested+0x4a/0x60
     [&lt;ffffffff81471ad7&gt;] genl_lock+0x17/0x20
     [&lt;ffffffff81471af6&gt;] genl_rcv+0x16/0x40
     [&lt;ffffffff8146ff72&gt;] netlink_unicast+0x2f2/0x310
     [&lt;ffffffff81470159&gt;] netlink_ack+0x109/0x1f0
     [&lt;ffffffff8147030b&gt;] netlink_rcv_skb+0xcb/0xd0
     [&lt;ffffffff81471b05&gt;] genl_rcv+0x25/0x40
     [&lt;ffffffff8146ff72&gt;] netlink_unicast+0x2f2/0x310
     [&lt;ffffffff8147134c&gt;] netlink_sendmsg+0x28c/0x3d0
     [&lt;ffffffff8143375f&gt;] sock_sendmsg+0xef/0x120
     [&lt;ffffffff81435766&gt;] ___sys_sendmsg+0x416/0x430
     [&lt;ffffffff81435949&gt;] __sys_sendmsg+0x49/0x90
     [&lt;ffffffff814359a9&gt;] sys_sendmsg+0x19/0x20
     [&lt;ffffffff8152432b&gt;] system_call_fastpath+0x16/0x1b
    
    Reported-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
