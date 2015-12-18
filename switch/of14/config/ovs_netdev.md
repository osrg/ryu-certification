---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4c52d569-7414-4576-b9da-fc793136ef50
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0de35eba-2e95-4c70-89f3-8e7c119d142b
controller          : [9a65c5f6-d6ba-4850-a33b-7bb66150db29]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [084c5544-9785-472b-9f39-ff5110eef8cb, 43259f01-db3b-4b7e-9128-e36ccbf5d787, 9f9f87a8-8176-46a5-a3d7-90717470c6e4, e1ba90f2-63b2-4b0e-91a5-f84543511415]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9a65c5f6-d6ba-4850-a33b-7bb66150db29
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9f9f87a8-8176-46a5-a3d7-90717470c6e4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7d70d6fc-fd85-4a59-910c-aa3fbb57430a]
name                : "eth21"

_uuid               : 084c5544-9785-472b-9f39-ff5110eef8cb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e66ec711-474d-4b24-9bac-33c54cb2a7fa]
name                : "eth22"

_uuid               : 43259f01-db3b-4b7e-9128-e36ccbf5d787
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d0ce9d8b-98f9-473f-b3c2-9901dd50a2ff]
name                : "eth23"

_uuid               : e1ba90f2-63b2-4b0e-91a5-f84543511415
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [83f871dd-f81f-4b83-87c2-bae8735a79b5]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7d70d6fc-fd85-4a59-910c-aa3fbb57430a
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
statistics          : {collisions=0, rx_bytes=42864012416, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28628366, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : e66ec711-474d-4b24-9bac-33c54cb2a7fa
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29487768870, tx_dropped=0, tx_errors=0, tx_packets=19682018}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 83f871dd-f81f-4b83-87c2-bae8735a79b5
admin_state         : down
duplex              : full
ifindex             : 696
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

_uuid               : d0ce9d8b-98f9-473f-b3c2-9901dd50a2ff
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6819844500, tx_dropped=0, tx_errors=0, tx_packets=4546563}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 8ab1170b06ddf33dfb06b0346d21f2e4380d8eea
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Thu Dec 17 13:56:39 2015 -0800
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Thu Dec 17 15:33:10 2015 -0800

    datapath: stt: Use RCU API to update stt-dev list.
    
    Following crash was reported for STT tunnel. I am not able to reproduce
    it, But the usage of wrong list manipulation API is likely culprit.
    
    ---8&lt;---
    IP: [&lt;ffffffffc0e731fd&gt;] nf_ip_hook+0xfd/0x180 [openvswitch]
    Oops: 0000 [#1] PREEMPT SMP
    Hardware name: VMware, Inc. VMware Virtual Platform/440BX
    RIP: 0010:[&lt;ffffffffc0e731fd&gt;]  [&lt;ffffffffc0e731fd&gt;] nf_ip_hook+0xfd/0x180 [openvswitch]
    RSP: 0018:ffff88043fd03cd0  EFLAGS: 00010206
    RAX: 0000000000000000 RBX: ffff8801008e2200 RCX: 0000000000000034
    RDX: 0000000000000110 RSI: ffff8801008e2200 RDI: ffff8801533a3880
    RBP: ffff88043fd03d00 R08: ffffffff90646d10 R09: ffff880164b27000
    R10: 0000000000000003 R11: ffff880155eb9dd8 R12: 0000000000000028
    R13: ffff8802283dc580 R14: 00000000000076b4 R15: ffff880013b20000
    FS:  00007ff5ba73b700&#40;0000&#41; GS:ffff88043fd00000&#40;0000&#41; knlGS:0000000000000000
    CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
    CR2: 0000000000000020 CR3: 000000037ff96000 CR4: 00000000000007e0
    Stack:
     ffff8801533a3890 ffff88043fd03d80 ffffffff90646d10 0000000000000000
     ffff880164b27000 ffff8801008e2200 ffff88043fd03d48 ffffffff9064050a
     ffffffff90d0f930 ffffffffc0e7ef80 0000000000000001 ffff8801008e2200
    Call Trace:
     &lt;IRQ&gt;
     [&lt;ffffffff90646d10&gt;] ? ip_rcv_finish+0x350/0x350
     [&lt;ffffffff9064050a&gt;] nf_iterate+0x9a/0xb0
     [&lt;ffffffff90646d10&gt;] ? ip_rcv_finish+0x350/0x350
     [&lt;ffffffff9064059c&gt;] nf_hook_slow+0x7c/0x120
     [&lt;ffffffff90646d10&gt;] ? ip_rcv_finish+0x350/0x350
     [&lt;ffffffff906470f3&gt;] ip_local_deliver+0x73/0x80
     [&lt;ffffffff90646a3d&gt;] ip_rcv_finish+0x7d/0x350
     [&lt;ffffffff90647398&gt;] ip_rcv+0x298/0x3d0
     [&lt;ffffffff9060fc56&gt;] __netif_receive_skb_core+0x696/0x880
     [&lt;ffffffff9060fe58&gt;] __netif_receive_skb+0x18/0x60
     [&lt;ffffffff90610b3e&gt;] process_backlog+0xae/0x180
     [&lt;ffffffff906102c2&gt;] net_rx_action+0x152/0x270
     [&lt;ffffffff9006d625&gt;] __do_softirq+0xf5/0x320
     [&lt;ffffffff9071d15c&gt;] do_softirq_own_stack+0x1c/0x30
    
    Reported-by: Joe Stringer &lt;joe@ovn.org&gt;
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@kernel.org&gt;
</pre>
