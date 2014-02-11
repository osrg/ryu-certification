---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
85fc3e4c-3636-4956-88ca-898adbc00432
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ff204806-beb3-4c0f-9452-3508ab8dd59c
controller          : [65f9985d-07d7-4eef-a284-fe0c2d54a7f2]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1b8e76ad-6358-4bf3-8c99-0d0b604beb7b, b8ee92ca-4582-48f1-9afa-a9393f06a753, fa226195-aac6-4702-99fe-afae2a78e64d]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 65f9985d-07d7-4eef-a284-fe0c2d54a7f2
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=296, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1b8e76ad-6358-4bf3-8c99-0d0b604beb7b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c6574d43-12f1-4055-9d76-3d7c1fc0a7db]
name                : br0

_uuid               : fa226195-aac6-4702-99fe-afae2a78e64d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e13007f3-682e-48d4-8987-df279847b5eb]
name                : eth8

_uuid               : b8ee92ca-4582-48f1-9afa-a9393f06a753
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b0aa8635-1d08-4d99-8d10-c3ebf4240756]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b0aa8635-1d08-4d99-8d10-c3ebf4240756
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=3056579005, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72567537, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : c6574d43-12f1-4055-9d76-3d7c1fc0a7db
admin_state         : up
duplex              : full
ifindex             : 224
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : e13007f3-682e-48d4-8987-df279847b5eb
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1687016, tx_dropped=0, tx_errors=0, tx_packets=18020}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c56fac1b678101b189e16f0462556c992feeffdc
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Feb 11 08:24:16 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Feb 11 08:24:16 2014 -0800

    ofproto-dpif-xlate: Make flows that match ICMP fields revalidate correctly.
    
    ICMPv4 and ICMPv6 have 8-bit type and code fields.  struct flow
    uses the low 8 bits of the 16-bit tp_src and tp_dst members to
    represent these fields.  The datapath interface, on the other hand,
    represents them with just 8 bits each.  This means that if the high 8
    bits of the masks for these fields somehow become set (meaning to
    match on the nonexistent high bits of these fields) during
    translation, then they will get chopped off by a round trip through
    the datapath, and revalidation will spot that as an inconsistency and
    delete the flow.  This commit avoids the problem by making sure that
    only the low 8 bits of either field can be unwildcarded for ICMP.
    
    This seems like the minimal fix for this problem, appropriate for
    backporting to earlier branches.  The root of the issue is that these high
    bits can get set in the match at all.  I have some leads on that, but they
    require more invasive changes elsewhere.
    
    Bug #23320.
    Reported-by: Krishna Miriyala &lt;miriyalak@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
