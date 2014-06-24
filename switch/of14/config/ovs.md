---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a74ecc2d-124a-4456-8277-d31b8a894f39
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ade4b6f1-05a0-476b-a573-5bf0cdd9799d
controller          : [af3f1a18-4ef4-4b28-a667-6b0d3f07adb8]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [3c468eb2-aeb2-434a-8577-840173ad146d, 518f6ac2-d55c-478b-8933-126eefcc582d, af4d7c9d-4ccf-429d-9a3b-b19af1d56ab8, e6260d4a-0845-4eac-88ab-b88de28b124b]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : af3f1a18-4ef4-4b28-a667-6b0d3f07adb8
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=25, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : af4d7c9d-4ccf-429d-9a3b-b19af1d56ab8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d1edcaaf-03ee-419b-ab96-29ce3aab143b]
name                : eth22

_uuid               : 3c468eb2-aeb2-434a-8577-840173ad146d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2adea0c9-8594-4f2d-a097-4b44d4d852f8]
name                : br0

_uuid               : 518f6ac2-d55c-478b-8933-126eefcc582d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5cbfbfe9-1e65-4d28-917b-3afabe3bf337]
name                : eth21

_uuid               : e6260d4a-0845-4eac-88ab-b88de28b124b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e03e833d-2877-4ec9-8ada-fa555808fbc3]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e03e833d-2877-4ec9-8ada-fa555808fbc3
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=3166524580, tx_dropped=0, tx_errors=0, tx_packets=10701635}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2adea0c9-8594-4f2d-a097-4b44d4d852f8
admin_state         : down
ifindex             : 621
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 5cbfbfe9-1e65-4d28-917b-3afabe3bf337
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
statistics          : {collisions=0, rx_bytes=309937619, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=89085953, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d1edcaaf-03ee-419b-ab96-29ce3aab143b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1114180108, tx_dropped=0, tx_errors=0, tx_packets=35147592}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7b900689deb559599c535ef2c4cf72ff14bf54f9
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Mon Jun 16 11:29:29 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Jun 23 17:06:56 2014 -0700

    ofproto: Break out monitor deletion code
    
    Break out monitor deletion code into a new function
    flow_monitor_delete which is paramatised over the id of
    the monitor to delete.
    
    This is in preparation for supporting OpenFlow1.4 flow monitor requests
    with delete and modify commands.
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
