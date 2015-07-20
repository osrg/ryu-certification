---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
815e2c41-4367-4e45-b0e4-02063b238585
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
_uuid               : 3eb619fb-8763-440c-ad3c-e15230473816
controller          : [4c2c6b23-b06d-4dc6-b8ca-d586ffc141d8]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [8f45aea5-c502-4807-95a5-09e76cf60b05, 9b50b390-4d2e-4160-9a1c-e819d4ded6da, c0dc9a23-c125-4d56-b43f-1990678d5b87, ef6f0332-9f07-444b-85a2-3a47e2193abb]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4c2c6b23-b06d-4dc6-b8ca-d586ffc141d8
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9b50b390-4d2e-4160-9a1c-e819d4ded6da
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [26730b3c-3d45-4d69-9764-f4bfa23e6722]
name                : "eth22"

_uuid               : 8f45aea5-c502-4807-95a5-09e76cf60b05
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f1e8eda1-4214-4ede-a6c5-bef02f0d17c4]
name                : "br0"

_uuid               : ef6f0332-9f07-444b-85a2-3a47e2193abb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0b7ff9f6-88f9-4ca9-aa06-f936d1d849d3]
name                : "eth21"

_uuid               : c0dc9a23-c125-4d56-b43f-1990678d5b87
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a0f30ea1-fce3-4900-bfcd-f86c8c3931ad]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 26730b3c-3d45-4d69-9764-f4bfa23e6722
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

_uuid               : a0f30ea1-fce3-4900-bfcd-f86c8c3931ad
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

_uuid               : f1e8eda1-4214-4ede-a6c5-bef02f0d17c4
admin_state         : down
duplex              : full
ifindex             : 267
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

_uuid               : 0b7ff9f6-88f9-4ca9-aa06-f936d1d849d3
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
commit 38876d31f2283eaf71f4c8acab4b2dad538019ef
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Sun Jul 19 23:13:14 2015 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Mon Jul 20 10:19:12 2015 -0700

    ofpbuf: Update msg when resizing ofpbuf.
    
    Commit 6fd6ed7 &#40;ofpbuf: Simplify ofpbuf API.&#41; introduced the
    'header' and 'msg' pointers to 'struct ofpbuf'.  However, we
    forget to update the 'msg' pointer when resizing ofpbuf.
    
    This bug could cause serious issue.  For example, in the function
    ofputil_encode_nx_packet_in&#40;&#41;, the 'msg' pointer is populated in
    ofpraw_alloc_xid&#40;&#41; when creating the ofpbuf .  Later, the ofpbuf
    memory can be reallocated due to the writing to the ofpbuf.
    However, since the 'msg' pointer is not updated, the later use of
    the 'ofpbuf-&gt;msg' will end up writing to either free'ed memory or
    memory allocated for other struct.
    
    This commit fixes the bug by always updating the 'header' and
    'msg' pointers when the ofpbuf is resized.  Also, a simple test
    is added.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
