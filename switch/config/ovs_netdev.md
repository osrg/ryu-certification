---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4642bd7d-e6fa-45be-b40b-e89044918699
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 44ee3f9a-7328-40d3-b698-29872cc8fa13
controller          : [25b0d875-2254-4b84-93f9-d551dd9a3a7e]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2bf40237-d218-4444-974b-4e2eb47e7a7a, 6042fd37-fcca-451c-8abf-f6cbaab9e7c4, d4449cb8-e0b1-441b-856d-ae4457320f2b, ea6eac8b-0f07-43fb-bb33-6543c3b88d0c]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 25b0d875-2254-4b84-93f9-d551dd9a3a7e
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="5", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d4449cb8-e0b1-441b-856d-ae4457320f2b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8625af94-5258-480b-b80d-a812f02a76fb]
name                : "eth23"

_uuid               : ea6eac8b-0f07-43fb-bb33-6543c3b88d0c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3060ea57-f96c-4e62-843a-1157e010882e]
name                : "eth22"

_uuid               : 2bf40237-d218-4444-974b-4e2eb47e7a7a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a2f92c88-697f-4c08-8b5c-94b9acc382c0]
name                : "eth21"

_uuid               : 6042fd37-fcca-451c-8abf-f6cbaab9e7c4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e47aa165-5280-4482-96ed-2cc3265957f5]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8625af94-5258-480b-b80d-a812f02a76fb
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

_uuid               : a2f92c88-697f-4c08-8b5c-94b9acc382c0
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
statistics          : {collisions=0, rx_bytes=48012771604, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=32089807, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : e47aa165-5280-4482-96ed-2cc3265957f5
admin_state         : down
duplex              : full
ifindex             : 868
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

_uuid               : 3060ea57-f96c-4e62-843a-1157e010882e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31805463706, tx_dropped=0, tx_errors=0, tx_packets=21241255}
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
