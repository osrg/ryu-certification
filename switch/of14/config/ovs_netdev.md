---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c2739ebd-e900-47d9-84e3-ef594934a8fc
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ba636f03-8904-40a4-b047-c8cf109b418e
controller          : [bdb31cb3-de71-476f-8754-a3cb4b04720d]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [573ef36c-1de2-4f5c-94ce-06ca0d9e3bc2, 6caf78f0-4b43-409b-b4ba-b092961a1b1a, 73aaf7aa-ffd4-4808-984c-3c432f6ecd07, 97c7592f-3741-4019-9ba3-cc8af2b46470]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : bdb31cb3-de71-476f-8754-a3cb4b04720d
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="752", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 573ef36c-1de2-4f5c-94ce-06ca0d9e3bc2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cc8dc64a-255f-4f00-b948-7fd60da3caca]
name                : "br0"

_uuid               : 6caf78f0-4b43-409b-b4ba-b092961a1b1a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2be051ae-af1d-4a91-ac65-643f91832056]
name                : "eth22"

_uuid               : 73aaf7aa-ffd4-4808-984c-3c432f6ecd07
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2bb3e467-17c8-42f0-bb07-3fe93c2c6c44]
name                : "eth21"

_uuid               : 97c7592f-3741-4019-9ba3-cc8af2b46470
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [203d2784-3cca-484c-939b-c9418495faa9]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 203d2784-3cca-484c-939b-c9418495faa9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3532536000, tx_dropped=0, tx_errors=0, tx_packets=2355024}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 2be051ae-af1d-4a91-ac65-643f91832056
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=27454772866, tx_dropped=0, tx_errors=0, tx_packets=18315536}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : cc8dc64a-255f-4f00-b948-7fd60da3caca
admin_state         : down
duplex              : full
ifindex             : 577
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

_uuid               : 2bb3e467-17c8-42f0-bb07-3fe93c2c6c44
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
statistics          : {collisions=0, rx_bytes=38429020683, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=25647228, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9975d7beb36ab3aadfd07c9d566f8d3d1d340fc4
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Oct 16 23:43:58 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Oct 16 23:52:41 2015 -0700

    ovn: Implement basic logical L3 routing.
    
    This implements basic logical L3 routing.  It has a lot of caveats,
    including the following regarding testing:
    
       * Only single-router hops have been tested.  Chains or trees of
         logical routers may work but definitely need testing and may
         need a little extra code.
    
       * No testing of logical router ARP replies.
    
       * Not enough testing in general.
    
    ovn/TODO describes a lot of other caveats in terms of the work needed
    to fix them.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
