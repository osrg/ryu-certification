---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1a367307-de91-475b-b680-57653d884a31
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 78e27ccf-afd9-4371-8407-aaf0539414a5
controller          : [d463a847-1ab6-4fdd-9a90-c3fa0c6177b8]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3af725fc-3f54-499c-913f-e4c8e5d52be0, 5e01da21-ee27-446a-b1fd-8b7230fb6c38, 696f528c-9957-4986-8aca-75e24d78d3d8, 8305d779-5d8c-4fdf-aa83-db163764faa4]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d463a847-1ab6-4fdd-9a90-c3fa0c6177b8
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 696f528c-9957-4986-8aca-75e24d78d3d8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ceb42364-9f6e-4427-9fc1-9b88b3c83743]
name                : "eth23"

_uuid               : 3af725fc-3f54-499c-913f-e4c8e5d52be0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c0eab948-1d1f-43bf-9561-387a5dcde64d]
name                : "eth21"

_uuid               : 8305d779-5d8c-4fdf-aa83-db163764faa4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3422c364-33ad-4a7b-a121-a86045b58a0c]
name                : "eth22"

_uuid               : 5e01da21-ee27-446a-b1fd-8b7230fb6c38
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7bdf8668-7844-4011-9037-3d8b7fe0c2db]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3422c364-33ad-4a7b-a121-a86045b58a0c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29277459838, tx_dropped=0, tx_errors=0, tx_packets=19540529}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7bdf8668-7844-4011-9037-3d8b7fe0c2db
admin_state         : down
duplex              : full
ifindex             : 680
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

_uuid               : ceb42364-9f6e-4427-9fc1-9b88b3c83743
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6468639000, tx_dropped=0, tx_errors=0, tx_packets=4312426}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c0eab948-1d1f-43bf-9561-387a5dcde64d
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
statistics          : {collisions=0, rx_bytes=42395935852, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28313684, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit eb1746e63583509510978eeb0df62a1c160dfdb3
Author:     Daniele Venturino &lt;daniele.venturino@m3s.it&gt;
AuthorDate: Fri Dec 11 13:59:00 2015 +0100
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Mon Dec 14 05:12:34 2015 -0800

    AUTHORS: Add Carlo Andreotti
    
    Carlo was involved in the testing and validation processes of the Rapid
    Spanning Tree Implementation.
    
    I also updated the Copyright string in some files.
    
    Signed-off by: Daniele Venturino &lt;daniele.venturino@m3s.it&gt;
    
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
