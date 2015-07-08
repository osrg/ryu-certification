---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c1e90fa7-6f68-426d-a4f3-33856a658922
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 55763a49-ccda-4f52-956c-e7c185850d5b
controller          : [8f6740a4-0450-4fd4-9d56-6f07db9d86a5]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [513f3782-63ce-491b-8256-bdaa15b6ccd1, 94a11e78-b0d7-4fe7-8648-035641245289, b1f96fa4-da1f-4919-93a4-e8bf6dbe34ec, ef9b7e98-535b-464b-8d5b-d6754e077f53]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8f6740a4-0450-4fd4-9d56-6f07db9d86a5
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ef9b7e98-535b-464b-8d5b-d6754e077f53
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0418c0a7-2572-4501-9f91-b048969825d9]
name                : "br0"

_uuid               : 94a11e78-b0d7-4fe7-8648-035641245289
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1861c8a9-3625-454b-bab0-bd1c576918c3]
name                : "eth21"

_uuid               : b1f96fa4-da1f-4919-93a4-e8bf6dbe34ec
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1ba4004c-e3b1-407c-a430-0cac9be6db6d]
name                : "eth22"

_uuid               : 513f3782-63ce-491b-8256-bdaa15b6ccd1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4ea948ea-0261-41f2-9576-254958ecea7a]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1ba4004c-e3b1-407c-a430-0cac9be6db6d
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

_uuid               : 1861c8a9-3625-454b-bab0-bd1c576918c3
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

_uuid               : 4ea948ea-0261-41f2-9576-254958ecea7a
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

_uuid               : 0418c0a7-2572-4501-9f91-b048969825d9
admin_state         : down
duplex              : full
ifindex             : 233
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
commit 4249b5470e65e1665d448f471356a144accdea47
Author:     Jeroen van Bemmel &lt;jvb127@gmail.com&gt;
AuthorDate: Mon Jul 6 12:58:24 2015 -0500
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jul 8 08:33:27 2015 -0700

    hash: Add symmetric L3/L4 hash functions for multipath, bundle hashing.
    
    Signed-off-by: Jeroen van Bemmel &lt;jvb127@gmail.com&gt;
    [blp@nicira.com made code style fixes, expanded documentation]
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
