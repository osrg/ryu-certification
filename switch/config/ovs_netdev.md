---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
97e6bfb1-9cb7-4427-b936-9054a3d55896
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b4bd296a-0c2e-4f6f-b03f-faf5b5949590
controller          : [fb8b1c21-ff75-4fef-b416-dbaf168cbbe0]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [33b8374f-96e4-4be1-949a-b3be39840264, 41535542-f9e1-47f1-b342-b14844bc3118, 42e7b44d-42c0-402b-8e32-6d8bb6e6cb32, 85109eac-42fc-4cd5-a644-ff97e4465c38]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : fb8b1c21-ff75-4fef-b416-dbaf168cbbe0
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 85109eac-42fc-4cd5-a644-ff97e4465c38
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b26144cc-f9c6-4c1e-8fd0-a49d872e5524]
name                : "eth23"

_uuid               : 42e7b44d-42c0-402b-8e32-6d8bb6e6cb32
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3c41f65a-cdf1-4749-ab82-d833a4831b73]
name                : "eth22"

_uuid               : 41535542-f9e1-47f1-b342-b14844bc3118
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [138cacd2-fcc6-40a2-ad2f-e61ab970c9a9]
name                : "br0"

_uuid               : 33b8374f-96e4-4be1-949a-b3be39840264
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0c587802-8957-4a64-8c57-ddaacaec3779]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b26144cc-f9c6-4c1e-8fd0-a49d872e5524
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9626532000, tx_dropped=0, tx_errors=0, tx_packets=6417688}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 138cacd2-fcc6-40a2-ad2f-e61ab970c9a9
admin_state         : down
duplex              : full
ifindex             : 818
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

_uuid               : 0c587802-8957-4a64-8c57-ddaacaec3779
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
statistics          : {collisions=0, rx_bytes=46608541654, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31145758, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 3c41f65a-cdf1-4749-ab82-d833a4831b73
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31173075352, tx_dropped=0, tx_errors=0, tx_packets=20815811}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e8fed7d01ca6fb6c7e96faf2b831fcfa4552cb4a
Author:     William Tu &lt;u9012063@gmail.com&gt;
AuthorDate: Wed Feb 17 18:00:22 2016 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Mon Feb 22 10:04:03 2016 -0800

    gcc: Fix compile errors due to anonymous union initilization.
    
    gcc 4.4.7 lets you initialize named fields, and assign to anonymous union members,
    but cannot statically initialize a named member of an anonymous union. This causes
    errors when doing make:
    fproto/fail-open.c: In function ‘send_bogus_packet_ins’:
    ofproto/fail-open.c:130: error: unknown field ‘pin’ specified in initializer
    ofproto/fail-open.c:131: error: unknown field ‘up’ specified in initializer
    ofproto/fail-open.c:132: error: unknown field ‘packet’ specified in initializer
    ofproto/fail-open.c:132: warning: missing braces around initializer
    ofproto/fail-open.c:132: warning: &#40;near initialization for ‘am.&lt;anonymous&gt;.pin.up’&#41;
    ofproto/fail-open.c:134: error: extra brace group at end of initializer
    
    Examaple: https://gcc.gnu.org/bugzilla/show_bug.cgi?id=42875
    We can either assign a name to the union or, in this patch, remove the unnecessary union.
    
    Signed-off-by: William Tu &lt;u9012063@gmail.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
