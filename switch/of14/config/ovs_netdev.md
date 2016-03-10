---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fb4a8bce-8384-4ae7-bea2-1909b8402d99
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
_uuid               : 5d4b3cbe-d67d-426c-9f1d-b9cc7b62d9f7
controller          : [1a14d969-e5f5-4615-9f82-e29acb08350f]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [8ab602c4-7288-4893-bcfe-9e54ef50f837, 9b7ded71-dcfa-4132-a6df-274e64e04453, ce6280f0-e4f2-4904-836a-15a1d032a59b, f1c215d9-889f-448c-808d-f2a79cc883b4]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 1a14d969-e5f5-4615-9f82-e29acb08350f
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ce6280f0-e4f2-4904-836a-15a1d032a59b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5e1241b7-086c-4044-954e-66d87e0a554e]
name                : "br0"

_uuid               : 8ab602c4-7288-4893-bcfe-9e54ef50f837
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c7414701-5f53-4963-9adb-982dedeb022c]
name                : "eth21"

_uuid               : f1c215d9-889f-448c-808d-f2a79cc883b4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [48eb1c37-f033-44d4-93c5-9bb53994a52c]
name                : "eth22"

_uuid               : 9b7ded71-dcfa-4132-a6df-274e64e04453
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dff95bab-4b19-4682-a873-e67f162ddf2b]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c7414701-5f53-4963-9adb-982dedeb022c
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
statistics          : {collisions=0, rx_bytes=48012771862, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=32089810, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 5e1241b7-086c-4044-954e-66d87e0a554e
admin_state         : down
duplex              : full
ifindex             : 870
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

_uuid               : dff95bab-4b19-4682-a873-e67f162ddf2b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10678669500, tx_dropped=0, tx_errors=0, tx_packets=7119113}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 48eb1c37-f033-44d4-93c5-9bb53994a52c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31805463964, tx_dropped=0, tx_errors=0, tx_packets=21241258}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit b00b4a81490f2d6f7c546f31098383ef12a13436
Author:     Yuanhan Liu &lt;yuanhan.liu@linux.intel.com&gt;
AuthorDate: Tue Mar 8 09:50:48 2016 +0800
Commit:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
CommitDate: Wed Mar 9 17:28:21 2016 -0800

    netdev-dpdk: fix mbuf leaks
    
    mbufs could be chained &#40;by the &quot;next&quot; field of rte_mbuf struct&#41;, when
    an mbuf is not big enough to hold a big packet, say when TSO is enabled.
    
    rte_pktmbuf_free_seg&#40;&#41; frees the head mbuf only, leading mbuf leaks.
    This patch fix it by invoking the right API rte_pktmbuf_free&#40;&#41;, to
    free all mbufs in the chain.
    
    Signed-off-by: Yuanhan Liu &lt;yuanhan.liu@linux.intel.com&gt;
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>
