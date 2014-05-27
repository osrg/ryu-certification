---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7df39a9e-4b12-491e-9b46-502f8986df37
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 65508a06-8727-4b04-95cc-605336a34e10
controller          : [2405a245-591b-4b33-acf6-1a5e1e8122f9]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [37577b16-b9e0-4274-a840-e4c9ea3e9d50, 57d1738b-d731-461e-a4e1-15014898940d, ec7b8f74-c6dd-4ac5-b6d2-a5d416679e16, eea439da-e605-4199-a241-cbf18fe4c488]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2405a245-591b-4b33-acf6-1a5e1e8122f9
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=996, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ec7b8f74-c6dd-4ac5-b6d2-a5d416679e16
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d88316b7-5251-4f53-9d31-d9335f32ad45]
name                : br0

_uuid               : 37577b16-b9e0-4274-a840-e4c9ea3e9d50
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e73551f0-e114-4fef-b52a-e8fb626e0967]
name                : eth22

_uuid               : eea439da-e605-4199-a241-cbf18fe4c488
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [37b673aa-027c-4dde-bb42-ffb709ad45a9]
name                : eth21

_uuid               : 57d1738b-d731-461e-a4e1-15014898940d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [824a0d7b-810d-4125-8379-47ac2f4ae358]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e73551f0-e114-4fef-b52a-e8fb626e0967
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2616829966, tx_dropped=0, tx_errors=0, tx_packets=1753815}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 37b673aa-027c-4dde-bb42-ffb709ad45a9
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
statistics          : {collisions=0, rx_bytes=2063143091, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=4263416, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 824a0d7b-810d-4125-8379-47ac2f4ae358
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=216905204, tx_dropped=0, tx_errors=0, tx_packets=3007915}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d88316b7-5251-4f53-9d31-d9335f32ad45
admin_state         : down
duplex              : full
ifindex             : 224
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 930d5a45bd8493c0d4e1c9dd5482fe4dc6f9087d
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue May 27 08:50:09 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue May 27 08:50:09 2014 -0700

    AUTHORS: Add Lars Kellogg-Stedman.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
