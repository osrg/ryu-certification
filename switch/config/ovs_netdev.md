---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
99dd75ab-86a0-4cb1-805c-859a24bc1eba
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 148a1295-1889-48c9-962d-0ab7d1f3bda7
controller          : [c40ea68e-295b-494c-8eaa-f7da66812977]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [01e1f506-30eb-4cb3-b6be-cf2dfb1de470, 737b620b-6c9e-42c9-a354-01f92be70d21, a3755431-17f0-40d7-b8fd-e09aa4b620d1, d1fb5b6f-7894-431c-b6e1-f95a69a89bbf]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c40ea68e-295b-494c-8eaa-f7da66812977
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=667, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a3755431-17f0-40d7-b8fd-e09aa4b620d1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1bd21df3-93a3-4e96-beb8-54a6c5f0bb4a]
name                : eth21

_uuid               : 01e1f506-30eb-4cb3-b6be-cf2dfb1de470
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [db2a2554-973c-41ce-8a48-3f3b7fe7bc4b]
name                : br0

_uuid               : d1fb5b6f-7894-431c-b6e1-f95a69a89bbf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f0546157-7a52-4cce-9e3c-29c5bc241dfa]
name                : eth23

_uuid               : 737b620b-6c9e-42c9-a354-01f92be70d21
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ad4db6ae-5ad4-436e-9646-cc7cb233b912]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : db2a2554-973c-41ce-8a48-3f3b7fe7bc4b
admin_state         : down
duplex              : full
ifindex             : 156
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

_uuid               : ad4db6ae-5ad4-436e-9646-cc7cb233b912
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2024013650, tx_dropped=0, tx_errors=0, tx_packets=47183981}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f0546157-7a52-4cce-9e3c-29c5bc241dfa
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2112858704, tx_dropped=0, tx_errors=0, tx_packets=4271884}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 1bd21df3-93a3-4e96-beb8-54a6c5f0bb4a
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
statistics          : {collisions=0, rx_bytes=3991062813, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=74291533, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ac8c20812b88c4aae7a002420f54d1333e27f784
Author:     Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
AuthorDate: Fri Sep 19 16:20:01 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Fri Sep 19 16:50:17 2014 -0700

    dpif-netdev: Fix &#40;packet&#41; memory leaks in the slow path.
    
    If a packet didn't match a rule in the fast path classifier its memory was
    never freed. The issue was particularly clear with DPDK devices because it was
    not possible to process more than ~250000 DPDK mbufs in the slow path.
    
    This commit fixes the problem by:
    * calling dpif_packet_delete&#40;&#41; if the upcalls are disabled
    * passing may_steal==true to dp_netdev_execute_actions&#40;&#41; during normal upcall
      processing
    
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
