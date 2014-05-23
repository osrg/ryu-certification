---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6f03b3de-8e05-44e6-a646-b063e8ddae8c
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c080e359-cc4a-4f16-aecf-6a26ba0210b7
controller          : [832a405d-951a-44ec-8e4d-1bcbd0afba34]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [53f58142-170c-4bef-b04f-0672e792ea5d, 686d2146-c1c7-43a2-8699-9a998e4b169a, 9707dd1a-4a8f-40f7-87a3-55972db2d48f, e6411858-6796-4ee4-945e-30e512dd4398]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 832a405d-951a-44ec-8e4d-1bcbd0afba34
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=552, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e6411858-6796-4ee4-945e-30e512dd4398
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [db534197-06c5-4b82-8642-6bbfb35c8958]
name                : eth23

_uuid               : 9707dd1a-4a8f-40f7-87a3-55972db2d48f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6920cc20-6375-4d54-8cf3-162b61cd08cc]
name                : eth21

_uuid               : 686d2146-c1c7-43a2-8699-9a998e4b169a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a6a53e74-8d26-4354-951a-5f2a1056fd4b]
name                : br0

_uuid               : 53f58142-170c-4bef-b04f-0672e792ea5d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [260bb900-f9e2-4180-a893-29cea1aa8aca]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6920cc20-6375-4d54-8cf3-162b61cd08cc
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
statistics          : {collisions=0, rx_bytes=1361780296, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=3791303, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a6a53e74-8d26-4354-951a-5f2a1056fd4b
admin_state         : down
duplex              : full
ifindex             : 202
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

_uuid               : 260bb900-f9e2-4180-a893-29cea1aa8aca
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2320467968, tx_dropped=0, tx_errors=0, tx_packets=1554507}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : db534197-06c5-4b82-8642-6bbfb35c8958
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4013569500, tx_dropped=0, tx_errors=0, tx_packets=2675713}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 691d39b2f93bc6d6339de82d4aeca337ab6aed86
Author:     Ethan Jackson &lt;ethan@nicira.com&gt;
AuthorDate: Thu May 22 10:53:27 2014 -0700
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Fri May 23 10:58:19 2014 -0700

    upcall: Remove redundant xlate_actions_for_side_effects&#40;&#41;.
    
    As a result of commit a0bab87 &#40;ofproto: Remove per-flow miss hash
    table from upcall handler.&#41; we're guaranteed that every packet has had
    xlate_actions&#40;&#41; called on it at least once.  Therefore, there's no
    need to re-xlate slow path flows just to shove their packets through
    the system.
    
    This also may fix a bug discussed here:
    http://openvswitch.org/pipermail/discuss/2014-April/013670.html
    
    Signed-off-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Reported-by: Murphy McCauley &lt;murphy.mccauley@gmail.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
