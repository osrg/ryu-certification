---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2f629b0c-e3fd-47de-b4c7-b5884c8d9544
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 97e985c7-b56a-4452-bae5-1036aa4a07a0
controller          : [a075b007-4423-4a75-bf94-41f35b475778]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [74aa91d7-263a-473b-b89f-8ce08a920cdf, 9e9f69d7-56da-45ca-8919-8f392ad563d4, f2c3f9ce-ba69-4a16-9713-50a8c3b710ed, f7484058-7b07-4631-93e2-3bcd37483bdb]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a075b007-4423-4a75-bf94-41f35b475778
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="752", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f7484058-7b07-4631-93e2-3bcd37483bdb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bd6232e5-5365-4c79-9191-8e4943c321c6]
name                : "eth23"

_uuid               : f2c3f9ce-ba69-4a16-9713-50a8c3b710ed
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0116ec98-370a-43e8-8157-3ea9f339a1b9]
name                : "br0"

_uuid               : 74aa91d7-263a-473b-b89f-8ce08a920cdf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [97204470-7865-442d-823a-955d0d5778b0]
name                : "eth22"

_uuid               : 9e9f69d7-56da-45ca-8919-8f392ad563d4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9101a56a-279f-4228-81c0-43dd9f91fd34]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 97204470-7865-442d-823a-955d0d5778b0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=26823082474, tx_dropped=0, tx_errors=0, tx_packets=17891103}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 0116ec98-370a-43e8-8157-3ea9f339a1b9
admin_state         : down
duplex              : full
ifindex             : 553
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

_uuid               : bd6232e5-5365-4c79-9191-8e4943c321c6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2479735500, tx_dropped=0, tx_errors=0, tx_packets=1653157}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9101a56a-279f-4228-81c0-43dd9f91fd34
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
statistics          : {collisions=0, rx_bytes=37024828879, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=24703378, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fdb5945136ea033fa9dc7473b1c836d04a4be483
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Fri Oct 9 17:33:04 2015 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Fri Oct 9 17:33:04 2015 -0700

    AUTHORS: Add John Reumann.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
