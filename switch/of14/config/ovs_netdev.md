---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4026b690-e6a4-4f00-b48c-6a1cf6a988cc
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 9861b330-6fc6-4a56-afa0-c7b306454cdc
controller          : [fda482a4-9937-4a31-a3f4-c5e0ca58dea3]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [756be01f-8fe5-4548-8a95-03560bd69a38, 821fb4f4-cd4f-4549-ad28-dc32f2ca72e2, ca27f201-1d64-4ba0-b36f-f40351d9f92c, e3c2042a-c9fb-45da-a992-a31da0670131]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : fda482a4-9937-4a31-a3f4-c5e0ca58dea3
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="647", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 821fb4f4-cd4f-4549-ad28-dc32f2ca72e2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1b25e053-0817-440e-b06d-dc178136d796]
name                : "eth21"

_uuid               : ca27f201-1d64-4ba0-b36f-f40351d9f92c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [971597f6-6029-4013-b13a-0e9e786eb237]
name                : "br0"

_uuid               : e3c2042a-c9fb-45da-a992-a31da0670131
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bf5bd8d4-8eda-4dae-a1f9-270823057ae0]
name                : "eth23"

_uuid               : 756be01f-8fe5-4548-8a95-03560bd69a38
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [48f5a605-52b3-4289-b781-941beb9b9533]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : bf5bd8d4-8eda-4dae-a1f9-270823057ae0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=40669155000, tx_dropped=0, tx_errors=0, tx_packets=27112770}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 48f5a605-52b3-4289-b781-941beb9b9533
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=629996102467, tx_dropped=0, tx_errors=0, tx_packets=420160334}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 971597f6-6029-4013-b13a-0e9e786eb237
admin_state         : down
duplex              : full
ifindex             : 889
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

_uuid               : 1b25e053-0817-440e-b06d-dc178136d796
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
statistics          : {collisions=0, rx_bytes=1231257798361, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=821208914, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a75776e6091b8597d966bc1a1cabb150a2de08f0
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Tue Mar 31 09:19:58 2015 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Mon Apr 13 13:52:24 2015 -0700

    datapath: Update inner offsets when expanding headroom.
    
    skb protocol offsets are relative to the beginning of the
    buffer and therefore must be updated if the buffer size is
    expanded. Kernel functions do this automatically for existing
    fields but obviously not for anything that we backport. This
    introduces a wrapper for pskb_expand_head&#40;&#41; to update the
    inner protocol fields that we have backported.
    
    Without this, a kernel crash can be triggered with tunnel
    packets that do not have enough headroom and need to be
    segmented. pskb_expand_head&#40;&#41; is called in directly through
    skb_cow_head&#40;&#41; at the beginning of each of the tunnel transmit
    routines.
    
    Reported-by: Yinpeijun &lt;yinpeijun@huawei.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
