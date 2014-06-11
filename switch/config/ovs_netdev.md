---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
24ef6eec-897b-44c0-af39-5355efb4c829
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 1783bca5-27e7-434a-8856-03bb5277d708
controller          : [6d4969ed-b91c-4dd3-9c33-3f60d27af72e]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [44e3e575-7cde-4e2a-b509-c52bb59503cf, 70e9ded8-b0a4-45f2-a84b-86ba20de218a, d4aacc51-b018-4cc6-aeff-75f20b070d42, fe83cb96-8ef9-4b97-8e63-b68be11dcd33]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6d4969ed-b91c-4dd3-9c33-3f60d27af72e
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=966, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 70e9ded8-b0a4-45f2-a84b-86ba20de218a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1998e5d2-e671-459b-8a10-4ab7bc3685a6]
name                : eth23

_uuid               : d4aacc51-b018-4cc6-aeff-75f20b070d42
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ed1155e0-0840-4b1b-899b-49c4c47ce521]
name                : eth22

_uuid               : 44e3e575-7cde-4e2a-b509-c52bb59503cf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0044b4dc-7807-4ac0-a6c9-9fafefed2786]
name                : eth21

_uuid               : fe83cb96-8ef9-4b97-8e63-b68be11dcd33
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9a4ae8fa-1789-4b3b-ad14-d25b0194239a]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ed1155e0-0840-4b1b-899b-49c4c47ce521
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1382166798, tx_dropped=0, tx_errors=0, tx_packets=12398962}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0044b4dc-7807-4ac0-a6c9-9fafefed2786
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
statistics          : {collisions=0, rx_bytes=779265339, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26356005, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9a4ae8fa-1789-4b3b-ad14-d25b0194239a
admin_state         : down
duplex              : full
ifindex             : 437
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

_uuid               : 1998e5d2-e671-459b-8a10-4ab7bc3685a6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1777169908, tx_dropped=0, tx_errors=0, tx_packets=6911403}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e5e4b47cc244c0d7ee404d105a2f22d0b327ee23
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed Jun 11 09:14:54 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jun 11 09:14:54 2014 -0700

    Fix log message weird suffixes.
    
    I think these were leftovers from the removal of %z for MSVC that happened
    some time ago.
    
    VMware-BZ: 1265762
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Pritesh Kothari &lt;pritesh.kothari@cisco.com&gt;
</pre>
