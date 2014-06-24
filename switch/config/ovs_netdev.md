---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
02ae9916-3796-4c32-957a-35430ce4b3c3
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
_uuid               : bce56168-46d9-4404-85ac-e66d68640217
controller          : [1f85e700-773a-4dae-825a-d06c9561c226]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4bbe4831-511d-465f-9d9a-1b5b93a20605, 8024a3ac-b4f6-42ef-9610-5082d29af024, d74f114e-32a2-410f-a83e-e438b294012c, e8ef19b7-f552-45de-9b60-43e2474dfcc0]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 1f85e700-773a-4dae-825a-d06c9561c226
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=972, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8024a3ac-b4f6-42ef-9610-5082d29af024
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8c8dc292-b7b8-4ecc-9426-cfefdcd8fdbb]
name                : eth23

_uuid               : 4bbe4831-511d-465f-9d9a-1b5b93a20605
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ac05c57c-675e-4c07-9ca3-3441ee030469]
name                : eth22

_uuid               : d74f114e-32a2-410f-a83e-e438b294012c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [02d82337-3761-47fe-8fdf-68102d47f571]
name                : br0

_uuid               : e8ef19b7-f552-45de-9b60-43e2474dfcc0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [85f08e63-9bb0-4ce9-b259-888c0a436110]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ac05c57c-675e-4c07-9ca3-3441ee030469
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3370192632, tx_dropped=0, tx_errors=0, tx_packets=33787388}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8c8dc292-b7b8-4ecc-9426-cfefdcd8fdbb
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2844719080, tx_dropped=0, tx_errors=0, tx_packets=10487098}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 85f08e63-9bb0-4ce9-b259-888c0a436110
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
statistics          : {collisions=0, rx_bytes=1593125966, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=81348891, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 02d82337-3761-47fe-8fdf-68102d47f571
admin_state         : down
duplex              : full
ifindex             : 613
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
