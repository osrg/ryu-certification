---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
5ddb3202-2a80-4f59-abb3-c003634400fa
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e9fd6b43-db70-40d1-84b4-2df3e4087fef
controller          : [568e1289-0751-4e8a-909a-f76463ca3a20]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0c6b347f-d067-4bc3-869b-5c1c2266934e, 23431568-76c4-4a33-accb-9bec3f68abdc, 766eb14c-8ebb-4ef1-9038-e0e9d88260ab, ab94dce5-0ad8-4edf-bc4d-8a9800217cad]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 568e1289-0751-4e8a-909a-f76463ca3a20
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="747", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 766eb14c-8ebb-4ef1-9038-e0e9d88260ab
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3fa54ea1-7ce7-4401-a986-f46ed8cd7a48]
name                : "eth23"

_uuid               : 23431568-76c4-4a33-accb-9bec3f68abdc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6c8cc7e2-5f9b-48cb-ae88-6737da8c92a2]
name                : "eth22"

_uuid               : ab94dce5-0ad8-4edf-bc4d-8a9800217cad
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2d2c493a-376f-4b05-8617-3ba9b175a89a]
name                : "br0"

_uuid               : 0c6b347f-d067-4bc3-869b-5c1c2266934e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ff6479be-a33b-42c9-9fcd-26e217db722c]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3fa54ea1-7ce7-4401-a986-f46ed8cd7a48
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2216008500, tx_dropped=0, tx_errors=0, tx_packets=1477339}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 2d2c493a-376f-4b05-8617-3ba9b175a89a
admin_state         : down
duplex              : full
ifindex             : 547
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

_uuid               : ff6479be-a33b-42c9-9fcd-26e217db722c
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
statistics          : {collisions=0, rx_bytes=36673776904, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=24467416, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 6c8cc7e2-5f9b-48cb-ae88-6737da8c92a2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=26665689172, tx_dropped=0, tx_errors=0, tx_packets=17785349}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3ca600a3e1b2cc67128ff3cbda42e5adc0376e5c
Author:     Gurucharan Shetty &lt;shettyg@nicira.com&gt;
AuthorDate: Wed Sep 30 14:18:47 2015 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Thu Oct 8 08:41:47 2015 -0700

    poll-loop: Fix a bug while finding a poll node.
    
    When a poll_node is created, it gets either a 'fd' or
    a 'wevent' &#40;can't get both&#41;. When the poll_node is
    searched for previous creations on that 'fd' or 'wevent',
    the search criteria was wrong for Windows. In Windows,
    when a 'fd' is received in poll_create_node, we create a
    corresponding 'wevent'. So while searching for that 'fd',
    we should not look for 'wevent' in the hmap_node.
    
    Reported-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
