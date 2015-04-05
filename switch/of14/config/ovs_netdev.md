---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
56ca61f7-1998-4b79-b511-903a3b6e431d
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0ba2fe29-ebd1-4db8-b604-03753197100e
controller          : [65c5af8a-2b20-4808-94d9-100ec64e1549]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [119e30e3-7e1f-4bbe-958d-395bf3ad2280, 16185290-17b6-4b37-a001-919a0f315545, aebad27e-cb5b-4d32-801b-cd6041f3e815, f2291290-5ff0-4aef-8746-673343d64405]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 65c5af8a-2b20-4808-94d9-100ec64e1549
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="647", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f2291290-5ff0-4aef-8746-673343d64405
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d3a5cfc2-7d7c-41a3-ad5b-ccabf8437a7a]
name                : "eth23"

_uuid               : 16185290-17b6-4b37-a001-919a0f315545
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e15fb456-6b16-48af-bb7e-38b885e92a2d]
name                : "br0"

_uuid               : aebad27e-cb5b-4d32-801b-cd6041f3e815
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [43044812-1e85-405a-aa8e-87316e263009]
name                : "eth21"

_uuid               : 119e30e3-7e1f-4bbe-958d-395bf3ad2280
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cc1bfb6b-5ebe-41db-b16f-bcd0b783cbe7]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e15fb456-6b16-48af-bb7e-38b885e92a2d
admin_state         : down
duplex              : full
ifindex             : 863
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

_uuid               : 43044812-1e85-405a-aa8e-87316e263009
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
statistics          : {collisions=0, rx_bytes=1218496998815, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=812692602, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d3a5cfc2-7d7c-41a3-ad5b-ccabf8437a7a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=39570811500, tx_dropped=0, tx_errors=0, tx_packets=26380541}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : cc1bfb6b-5ebe-41db-b16f-bcd0b783cbe7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=619796003327, tx_dropped=0, tx_errors=0, tx_packets=413356166}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 31efbdb998b0267e245b8edc32b34c0dcc45e723
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Sun Apr 5 12:12:13 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Sun Apr 5 13:39:59 2015 -0700

    rhel: Package vport-*.ko in Fedora kernel package.
    
    Fixes a presumed build break due to unpackaged files.  &#40;Only &quot;presumed&quot; at
    this point because it is masked in the VMware build system by the similar
    XenServer build failure.&#41;
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
