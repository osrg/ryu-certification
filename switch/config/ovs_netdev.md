---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
018fd6d3-a666-47d9-b317-b2953447295f
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a49b85bb-a341-4aeb-ba8b-83ac2a1176be
controller          : [cc7e10ea-81f3-4a73-9c5d-07c1034928bb]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [07aa62d8-c87f-46a0-ba24-d03ba239d72d, 60731089-40a1-452f-818e-3df81f3105ac, 9e4ced1f-b303-47d9-b1a0-de9b11fc9446]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : cc7e10ea-81f3-4a73-9c5d-07c1034928bb
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=922, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 07aa62d8-c87f-46a0-ba24-d03ba239d72d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9923ac4a-74a0-495a-96e1-f6812bc41b3d]
name                : eth7

_uuid               : 60731089-40a1-452f-818e-3df81f3105ac
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f793fe23-fab8-4005-80b4-2146038d8377]
name                : eth8

_uuid               : 9e4ced1f-b303-47d9-b1a0-de9b11fc9446
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cc8a3a66-4acc-49aa-bffd-ebee275d1e78]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : cc8a3a66-4acc-49aa-bffd-ebee275d1e78
admin_state         : down
duplex              : full
ifindex             : 879
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 9923ac4a-74a0-495a-96e1-f6812bc41b3d
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=3073404736, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72738153, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : f793fe23-fab8-4005-80b4-2146038d8377
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6711783, tx_dropped=0, tx_errors=0, tx_packets=71543}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5e314e8e771345c11df811fc45d584911cbc1642
Author:     Lorand Jakab &lt;lojakab@cisco.com&gt;
AuthorDate: Fri Apr 4 11:09:52 2014 +0300
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Apr 4 08:08:31 2014 -0700

    ofpbuf: fix struct comment
    
    Signed-off-by: Lorand Jakab &lt;lojakab@cisco.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
