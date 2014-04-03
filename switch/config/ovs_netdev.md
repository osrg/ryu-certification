---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2a9ef104-fb5d-49b9-a3e4-b9dd37d9d487
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : db9d1a6e-c699-431f-bd7f-5b59a52b60fa
controller          : [18893778-292c-433c-832b-70163026440d]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [47df61e2-e38e-4a46-b0a7-074612b1b55d, 605121dc-3e3b-4ec9-8176-46d90808c1a3, 84a38054-7a0a-4718-b546-c26e71b95877]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 18893778-292c-433c-832b-70163026440d
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=302, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 84a38054-7a0a-4718-b546-c26e71b95877
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4196196b-40c5-4177-9118-a8903b8e35d7]
name                : eth7

_uuid               : 605121dc-3e3b-4ec9-8176-46d90808c1a3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c57c162e-25bb-493b-bc41-91de6a998936]
name                : br0

_uuid               : 47df61e2-e38e-4a46-b0a7-074612b1b55d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [354e2717-5f30-4ed1-a529-9ff36bb171d0]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c57c162e-25bb-493b-bc41-91de6a998936
admin_state         : up
duplex              : full
ifindex             : 863
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

_uuid               : 4196196b-40c5-4177-9118-a8903b8e35d7
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
statistics          : {collisions=0, rx_bytes=3073041790, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72734474, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 354e2717-5f30-4ed1-a529-9ff36bb171d0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6601079, tx_dropped=0, tx_errors=0, tx_packets=70364}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit cf3b7538666cd1efa314ce4944e4efdf3dd81d99
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Wed Apr 2 15:44:21 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Thu Apr 3 11:51:59 2014 -0700

    ofpbuf: Abstract 'l2' pointer and document usage conventions.
    
    Rename 'l2' to 'frame' and add new ofpbuf_set_frame() and ofpbuf_l2().
    ofpbuf_set_frame() alse resets all the layer offsets.  ofpbuf_l2()
    returns NULL if the packet has no Ethernet header, as indicated either
    by unset l3 offset or NULL frame pointer.  Callers of ofpbuf_l2() are
    supposed to check the return value, unless they can otherwise be sure
    that the packet has a valid Ethernet header.
    
    The recent commit 437d0d22 made some assumptions that were not valid
    regarding the use of the 'l2' pointer in rconn module and by
    compose_rarp().  This is now fixed as follows: rconn now relies on the
    fact that once OpenFlow messages are given to rconn for transport, the
    frame pointer is no longer needed to refer to the OpenFlow header; and
    compose_rarp() now sets the frame pointer and offsets as expected.
    
    In addition to storing network frames, ofpbufs are also used for
    handling OpenFlow messages and action lists.  lib/ofpbuf.h now has a
    comment documenting the current usage conventions and invariants.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
