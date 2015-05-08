---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
01388c68-c7a7-4992-a42e-60c20bef8929
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e94b77cc-9afe-4e65-84b6-a42d96725522
controller          : [08d6ed04-eacd-4527-acec-026b6ea7e49c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0a3e9a2b-f3e6-4762-9109-93dfc79505c5, 29cd7e2a-9a83-4054-b7e5-da7fcc1a43fc, 532a97d5-a905-48fc-9323-50bcfbc6b6f2, 5f8480da-d23f-4077-bef4-b9a6624e0f41]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 08d6ed04-eacd-4527-acec-026b6ea7e49c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="647", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 532a97d5-a905-48fc-9323-50bcfbc6b6f2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f1818556-4439-4011-91f0-b43471e130e1]
name                : "eth23"

_uuid               : 29cd7e2a-9a83-4054-b7e5-da7fcc1a43fc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d5b7ef44-c0d7-495a-bdf9-3de24e6252f8]
name                : "eth22"

_uuid               : 5f8480da-d23f-4077-bef4-b9a6624e0f41
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e9204bbf-3e67-48be-a5ec-5e399360751e]
name                : "eth21"

_uuid               : 0a3e9a2b-f3e6-4762-9109-93dfc79505c5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [55446906-b10f-450b-8fd8-51628f73bd66]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d5b7ef44-c0d7-495a-bdf9-3de24e6252f8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9675009424, tx_dropped=0, tx_errors=0, tx_packets=6451675}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f1818556-4439-4011-91f0-b43471e130e1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=397480500, tx_dropped=0, tx_errors=0, tx_packets=264987}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 55446906-b10f-450b-8fd8-51628f73bd66
admin_state         : down
duplex              : full
ifindex             : 35
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

_uuid               : e9204bbf-3e67-48be-a5ec-5e399360751e
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
statistics          : {collisions=0, rx_bytes=11811538946, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=7878332, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 36be51c5b09c97a62c342e8ff0bb2d1a33ea2b68
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri May 8 09:15:43 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri May 8 11:33:58 2015 -0700

    ofp-util: Use OFPGMFC_OUT_OF_BUCKETS for indirect groups with !=1 buckets.
    
    OpenFlow 1.3 says:
    
        If a switch cannot add the incoming group entry due to restrictions
        &#40;hardware or otherwise&#41; limiting the number of group buckets, it must
        refuse to add the group entry and must send an ofp_error_msg with
        OFPET_GROUP_MOD_FAILED type and OFPGMFC_OUT_OF_BUCKETS code.
    
    This indicates that OFPGMFC_OUT_OF_BUCKETS is appropriate for an indirect
    group with the wrong number of buckets, but OVS was using a different
    error.  This fixes the problem.
    
    ONF-JIRA: EXT-546
    Reported-by: Mrinmoy Das &lt;mrdas@ixiacom.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
