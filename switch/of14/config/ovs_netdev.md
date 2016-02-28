---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9375e578-3f61-443b-9a27-c20ae213a642
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c849605a-25be-424a-91f1-3b37ea398fa7
controller          : [0a1c607a-079a-4634-b43d-2b24719c8d0a]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [27f454fc-97c1-42b3-993f-0d51909719b1, 5088241f-8789-4eb6-9168-9376ba5d3100, c62a2ce0-208e-499b-93d4-ca3bef17c08e, f5b61cd3-17dd-481d-a7b2-30ff7cd3f02c]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0a1c607a-079a-4634-b43d-2b24719c8d0a
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="12", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c62a2ce0-208e-499b-93d4-ca3bef17c08e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f3f9f99b-9ea4-4f7a-a54b-8813b1c9b033]
name                : "br0"

_uuid               : 27f454fc-97c1-42b3-993f-0d51909719b1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7c600c88-34c7-40ad-bf2a-8d52c9d37ccd]
name                : "eth21"

_uuid               : f5b61cd3-17dd-481d-a7b2-30ff7cd3f02c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5f62260b-f175-41a8-b5db-eb6b9fa735ec]
name                : "eth23"

_uuid               : 5088241f-8789-4eb6-9168-9376ba5d3100
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [24f5e4c2-50a6-46ed-bff8-74a3c1b19083]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7c600c88-34c7-40ad-bf2a-8d52c9d37ccd
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
statistics          : {collisions=0, rx_bytes=47193640125, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31539118, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 24f5e4c2-50a6-46ed-bff8-74a3c1b19083
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31436431283, tx_dropped=0, tx_errors=0, tx_packets=20992991}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 5f62260b-f175-41a8-b5db-eb6b9fa735ec
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10065061500, tx_dropped=0, tx_errors=0, tx_packets=6710041}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f3f9f99b-9ea4-4f7a-a54b-8813b1c9b033
admin_state         : down
duplex              : full
ifindex             : 842
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
commit 4be4d22c33f67c2154d4252746970ef1032c58a6
Author:     Mark Kavanagh &lt;mark.b.kavanagh@intel.com&gt;
AuthorDate: Fri Feb 19 11:25:11 2016 +0000
Commit:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
CommitDate: Sun Feb 28 11:19:37 2016 -0800

    netdev-dpdk: clean up mbuf initialization
    
    Current mbuf initialization relies on magic numbers and does not
    accomodate mbufs of different sizes.
    
    Resolve this issue by ensuring that mbufs are always aligned to a 1k
    boundary &#40;a typical DPDK NIC Rx buffer alignment&#41;.
    
    Signed-off-by: Mark Kavanagh &lt;mark.b.kavanagh@intel.com&gt;
    Acked-by: Flavio Leitner &lt;fbl@sysclose.org&gt;
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>
