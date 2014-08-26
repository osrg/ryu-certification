---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
95a4a0b1-2dc2-465f-b61f-374e81b012e3
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a7880d2f-6464-40c9-a5c3-da4039435d91
controller          : [78248cc0-8014-43b3-b47b-56634e9dbd40]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [066cc1d2-330c-405a-886a-6f6817b2608f, 2cb78035-3411-49e3-961f-b3e72581c357, 4cbcfdc0-3317-44bc-9f93-8eccecb8c0cd, b6ede426-ae43-4c44-8236-a84dd5b59b4b]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 78248cc0-8014-43b3-b47b-56634e9dbd40
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=832, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4cbcfdc0-3317-44bc-9f93-8eccecb8c0cd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [287fe657-0443-44cf-a001-653ef4f41551]
name                : eth22

_uuid               : 2cb78035-3411-49e3-961f-b3e72581c357
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dc577d48-0aa8-48ac-a0ea-66e1dfb0b99e]
name                : eth21

_uuid               : b6ede426-ae43-4c44-8236-a84dd5b59b4b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f6ac7e70-27eb-4a56-a89d-67c020e292ce]
name                : br0

_uuid               : 066cc1d2-330c-405a-886a-6f6817b2608f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e67b01fd-3c97-4e01-a836-65ee4d127491]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f6ac7e70-27eb-4a56-a89d-67c020e292ce
admin_state         : down
duplex              : full
ifindex             : 63
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

_uuid               : dc577d48-0aa8-48ac-a0ea-66e1dfb0b99e
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
statistics          : {collisions=0, rx_bytes=155790612, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=17297543, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e67b01fd-3c97-4e01-a836-65ee4d127491
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1939972500, tx_dropped=0, tx_errors=0, tx_packets=1293315}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 287fe657-0443-44cf-a001-653ef4f41551
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2155619036, tx_dropped=0, tx_errors=0, tx_packets=12896580}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit caac88029f94a9b1141ad3acf8c504441b26ce1d
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Aug 26 11:44:28 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Aug 26 11:44:28 2014 -0700

    AUTHORS: Add Ed Swierk.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
