---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
43c2929f-9dbe-45ff-a933-b61ad889a6dd
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0c89a6e4-6b81-4cdb-87f4-1c7be8cb1453
controller          : [126115e3-2ad9-42c3-8e5e-b04bc346d7d7]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [241cf3c4-8fe2-4388-b16a-c260e2836d75, 4fd7e902-e71a-416d-a7d4-540252ae4d9b, 538c9745-96a2-415c-9834-0029e3b72455, bb286149-0611-4c96-a4a9-523550716034]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 126115e3-2ad9-42c3-8e5e-b04bc346d7d7
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=961, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 241cf3c4-8fe2-4388-b16a-c260e2836d75
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [75dd3a86-f974-47ce-91b7-c23e6f012eb1]
name                : eth22

_uuid               : bb286149-0611-4c96-a4a9-523550716034
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c4121ab9-d086-44d3-b1e0-fc20e94dce5a]
name                : eth21

_uuid               : 538c9745-96a2-415c-9834-0029e3b72455
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3bb987dd-2b65-40cd-ae69-7b7da60ec8a3]
name                : eth23

_uuid               : 4fd7e902-e71a-416d-a7d4-540252ae4d9b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1187f5fa-f98d-4aeb-9f49-1ba2da0431ca]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c4121ab9-d086-44d3-b1e0-fc20e94dce5a
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
statistics          : {collisions=0, rx_bytes=3866580767, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=11218223, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3bb987dd-2b65-40cd-ae69-7b7da60ec8a3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4194425204, tx_dropped=0, tx_errors=0, tx_packets=5659595}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 1187f5fa-f98d-4aeb-9f49-1ba2da0431ca
admin_state         : down
duplex              : full
ifindex             : 370
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

_uuid               : 75dd3a86-f974-47ce-91b7-c23e6f012eb1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2885153492, tx_dropped=0, tx_errors=0, tx_packets=4804802}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 143859ec63d45e5184356984dbf10c142e0ded39
Author:     Ryan Wilson &lt;wryan@nicira.com&gt;
AuthorDate: Wed Jun 4 13:49:06 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Wed Jun 4 15:48:30 2014 -0700

    dpif-netdev: Upcall: Remove an extra memcpy of packet data.
    
    When a bridge of datatype type netdev receives a packet, it
    copies the packet from the NIC to a buffer in userspace.
    Currently, when making an upcall, the packet is again copied
    to the upcall's buffer. However, this extra copy is not
    necessary when the datapath exists in userspace as the upcall
    can directly access the packet data.
    
    This patch eliminates this extra copy of the packet data in
    most cases. In cases where the packet may still be used later
    by callers of dp_netdev_execute_actions, making a copy of the
    packet data is still necessary.
    
    This patch also adds a dpdk_buf field to 'struct ofpbuf' when
    using DPDK. This field holds a pointer to the allocated DPDK
    buffer in the rte_mempool. Thus, an upcall packet ofpbuf
    allocated on the stack can now share data and free memory of
    a rte_mempool allocated ofpbuf.
    
    Signed-off-by: Ryan Wilson &lt;wryan@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
