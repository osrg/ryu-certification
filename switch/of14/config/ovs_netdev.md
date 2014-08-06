---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
86b8a3af-49a9-4800-bbaa-12661882a46d
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 43775d81-0b64-4524-93b5-f357e9224dd0
controller          : [a7ceca8e-5d27-4821-acf7-aa56015042d4]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0740c8e8-029f-4bdf-a048-86a38cfa1126, 6907c24e-5891-4c3b-84ca-453d436d9bcc, a88ef752-620b-4537-a516-97278681b076, c45c1341-57fd-4bbe-b5e6-17114f087eba]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a7ceca8e-5d27-4821-acf7-aa56015042d4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=687, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0740c8e8-029f-4bdf-a048-86a38cfa1126
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c577f935-f78b-47a5-8a48-68fc328b8499]
name                : eth21

_uuid               : c45c1341-57fd-4bbe-b5e6-17114f087eba
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [68fcb3b7-6e34-4914-a454-0c3321da1bc9]
name                : eth22

_uuid               : 6907c24e-5891-4c3b-84ca-453d436d9bcc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9d66bab8-d8db-4e8a-8d1d-0159bd2ddab5]
name                : eth23

_uuid               : a88ef752-620b-4537-a516-97278681b076
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bb36e1b2-e91d-4324-b8a0-c5c9cbaa4348]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9d66bab8-d8db-4e8a-8d1d-0159bd2ddab5
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2796504000, tx_dropped=0, tx_errors=0, tx_packets=1864336}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c577f935-f78b-47a5-8a48-68fc328b8499
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=2190873411, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=84525716, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : bb36e1b2-e91d-4324-b8a0-c5c9cbaa4348
admin_state         : down
duplex              : full
ifindex             : 79
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 68fcb3b7-6e34-4914-a454-0c3321da1bc9
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1270605580, tx_dropped=0, tx_errors=0, tx_packets=49536079}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fb42720ed20a4268d44df3f39e3ec5fd00261e28
Author:     Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
AuthorDate: Thu Aug 7 01:35:11 2014 +0000
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Wed Aug 6 10:58:22 2014 -0700

    test-atomic: Fix warnings for GCC4.9 and sparse
    
    There's no reason for the local variable 'old_count' to be atomic. In fact, if
    it is atomic it triggers a GCC4.9 warning &#40;Wunused-value&#41;
    The global variables 'a' and 'paux' could be static, according to sparse.
    
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
