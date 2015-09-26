---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ba78f0a9-6b2a-404d-89dc-99de10a2f2f5
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 06394d0c-d31a-4fd4-ae68-32d240546fe4
controller          : [b69e07b0-894d-4270-a7a6-19c8072d8b05]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [02c72172-62fb-4ae9-8b00-84058382e9b6, 3a3e975f-4321-4562-9013-10add8923f68, bec41cf4-de1a-4ea0-b797-0d8379c85cfa, fd3f4ff5-1d68-451e-977d-86c06e6a994e]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b69e07b0-894d-4270-a7a6-19c8072d8b05
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : bec41cf4-de1a-4ea0-b797-0d8379c85cfa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4c54d178-7c80-4683-b663-9e0e68a92fab]
name                : "br0"

_uuid               : fd3f4ff5-1d68-451e-977d-86c06e6a994e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5f9f0dfd-b546-416e-94db-a6892d151fbe]
name                : "eth22"

_uuid               : 02c72172-62fb-4ae9-8b00-84058382e9b6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8ff1ad67-2286-495a-afb1-1e1a35ac1e5c]
name                : "eth21"

_uuid               : 3a3e975f-4321-4562-9013-10add8923f68
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b9032397-f351-4a4d-bdd9-a8eddfe7e057]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4c54d178-7c80-4683-b663-9e0e68a92fab
admin_state         : down
duplex              : full
ifindex             : 501
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

_uuid               : 5f9f0dfd-b546-416e-94db-a6892d151fbe
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

_uuid               : b9032397-f351-4a4d-bdd9-a8eddfe7e057
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

_uuid               : 8ff1ad67-2286-495a-afb1-1e1a35ac1e5c
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a2cf7524787d57c7a6b616f84ce033faf68df0aa
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Fri Sep 25 16:25:10 2015 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Fri Sep 25 19:50:02 2015 -0700

    datapath: Backport &quot;skbuff: Fix skb checksum flag on skb pull&quot;
    
    Upstream commit:
    
        VXLAN device can receive skb with checksum partial. But the checksum
        offset could be in outer header which is pulled on receive. This results
        in negative checksum offset for the skb. Such skb can cause the assert
        failure in skb_checksum_help&#40;&#41;. Following patch fixes the bug by setting
        checksum-none while pulling outer header.
    
        Following is the kernel panic msg from old kernel hitting the bug.
    
        ------------[ cut here ]------------
        kernel BUG at net/core/dev.c:1906!
        RIP: 0010:[&lt;ffffffff81518034&gt;] skb_checksum_help+0x144/0x150
        Call Trace:
        &lt;IRQ&gt;
        [&lt;ffffffffa0164c28&gt;] queue_userspace_packet+0x408/0x470 [openvswitch]
        [&lt;ffffffffa016614d&gt;] ovs_dp_upcall+0x5d/0x60 [openvswitch]
        [&lt;ffffffffa0166236&gt;] ovs_dp_process_packet_with_key+0xe6/0x100 [openvswitch]
        [&lt;ffffffffa016629b&gt;] ovs_dp_process_received_packet+0x4b/0x80 [openvswitch]
        [&lt;ffffffffa016c51a&gt;] ovs_vport_receive+0x2a/0x30 [openvswitch]
        [&lt;ffffffffa0171383&gt;] vxlan_rcv+0x53/0x60 [openvswitch]
        [&lt;ffffffffa01734cb&gt;] vxlan_udp_encap_recv+0x8b/0xf0 [openvswitch]
        [&lt;ffffffff8157addc&gt;] udp_queue_rcv_skb+0x2dc/0x3b0
        [&lt;ffffffff8157b56f&gt;] __udp4_lib_rcv+0x1cf/0x6c0
        [&lt;ffffffff8157ba7a&gt;] udp_rcv+0x1a/0x20
        [&lt;ffffffff8154fdbd&gt;] ip_local_deliver_finish+0xdd/0x280
        [&lt;ffffffff81550128&gt;] ip_local_deliver+0x88/0x90
        [&lt;ffffffff8154fa7d&gt;] ip_rcv_finish+0x10d/0x370
        [&lt;ffffffff81550365&gt;] ip_rcv+0x235/0x300
        [&lt;ffffffff8151ba1d&gt;] __netif_receive_skb+0x55d/0x620
        [&lt;ffffffff8151c360&gt;] netif_receive_skb+0x80/0x90
        [&lt;ffffffff81459935&gt;] virtnet_poll+0x555/0x6f0
        [&lt;ffffffff8151cd04&gt;] net_rx_action+0x134/0x290
        [&lt;ffffffff810683d8&gt;] __do_softirq+0xa8/0x210
        [&lt;ffffffff8162fe6c&gt;] call_softirq+0x1c/0x30
        [&lt;ffffffff810161a5&gt;] do_softirq+0x65/0xa0
        [&lt;ffffffff810687be&gt;] irq_exit+0x8e/0xb0
        [&lt;ffffffff81630733&gt;] do_IRQ+0x63/0xe0
        [&lt;ffffffff81625f2e&gt;] common_interrupt+0x6e/0x6e
    
        Reported-by: Anupam Chanda &lt;achanda@vmware.com&gt;
        Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
        Acked-by: Tom Herbert &lt;tom@herbertland.com&gt;
        Signed-off-by: David S. Miller &lt;davem@davemloft.net&gt;
    
    Upstream: 6ae459bdaae &#40;&quot;skbuff: Fix skb checksum flag on skb pull&quot;&#41;
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
