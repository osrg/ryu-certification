---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0ad0e78e-c19a-496f-842e-65e644ce5399
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
_uuid               : 19ec2785-2326-48e7-bc7e-6d7fe3a46d59
controller          : [621c480c-4910-46ea-9c76-b7d31b2d081b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [752c4dab-0285-4c17-ad3c-12d6bddafaef, 950c6749-3b00-42db-8a96-e4809379a977, dbf438e6-a8fc-4cb3-96b8-69dff9e88f35, f3f4d31b-9003-47c2-9094-8cec4351e12e]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 621c480c-4910-46ea-9c76-b7d31b2d081b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 950c6749-3b00-42db-8a96-e4809379a977
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [47dd4580-5542-4bed-9efe-c502d65045af]
name                : "eth22"

_uuid               : dbf438e6-a8fc-4cb3-96b8-69dff9e88f35
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [893e97a7-6bec-4a50-932e-0d169c4c2143]
name                : "eth23"

_uuid               : 752c4dab-0285-4c17-ad3c-12d6bddafaef
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [21c87dd5-405a-4218-8619-f2d5f0c8a773]
name                : "eth21"

_uuid               : f3f4d31b-9003-47c2-9094-8cec4351e12e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [913dbba3-eb19-4904-b9d7-f1f1a526537e]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 47dd4580-5542-4bed-9efe-c502d65045af
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

_uuid               : 21c87dd5-405a-4218-8619-f2d5f0c8a773
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

_uuid               : 893e97a7-6bec-4a50-932e-0d169c4c2143
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

_uuid               : 913dbba3-eb19-4904-b9d7-f1f1a526537e
admin_state         : down
duplex              : full
ifindex             : 66
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
commit 048963aa8507f3627bf3c9b4cbe4be4a46845b42
Author:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
AuthorDate: Wed Apr 22 19:22:52 2015 +0100
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Thu May 21 14:00:24 2015 -0700

    dpif-netdev: Reset RSS hash when recirculating.
    
    Having the same RSS hash after recirculation can cause unnecessary
    collisions in the exact match cache.  A simple solution is to rehash it
    with the recirculation depth if it is non-zero.
    
    Suggested-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    Signed-off-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
