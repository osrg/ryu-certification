---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2fb557a7-8fdb-4116-8afc-64135c90aa89
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e00f3122-4856-4d54-a1b0-220ee08b096b
controller          : [c2509c60-4cfa-4a04-9bd6-02f77a743f2c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [6683f97b-f043-438e-a68f-5e8a2ea324e3, 96691adb-a0ad-4fdf-a921-c4a6127e2666, fd3da87c-7bef-4ea6-9f1e-064236ec55cc]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c2509c60-4cfa-4a04-9bd6-02f77a743f2c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=302, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : fd3da87c-7bef-4ea6-9f1e-064236ec55cc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0898c262-0055-4e58-969b-509e1476b2ef]
name                : eth7

_uuid               : 6683f97b-f043-438e-a68f-5e8a2ea324e3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [80d78576-d9f7-4c16-92f7-3ff8764d3f69]
name                : eth8

_uuid               : 96691adb-a0ad-4fdf-a921-c4a6127e2666
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f972c3d8-9eb0-4b71-99f8-109153bd2100]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f972c3d8-9eb0-4b71-99f8-109153bd2100
admin_state         : up
duplex              : full
ifindex             : 103
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 80d78576-d9f7-4c16-92f7-3ff8764d3f69
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=781712, tx_dropped=0, tx_errors=0, tx_packets=8414}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 0898c262-0055-4e58-969b-509e1476b2ef
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
statistics          : {collisions=0, rx_bytes=2480070, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=25080, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ddd43de9ba729023dbee897a330727dfa9a6a7a6
Author:     Helmut Schaa &lt;helmut.schaa@googlemail.com&gt;
AuthorDate: Fri Dec 6 16:18:42 2013 +0100
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jan 16 17:43:11 2014 -0800

    vswitchd: Inherit parents mac address for fake bridges
    
    When adding a physical port to the main bridge the mac address
    of the bridge is updated. We can do the same for fake bridges by
    copying the mac address of the parent bridge.
    
    There exists only one fake bridge per vlan, hence it is safe
    to copy the mac address of the parent bridge.
    
    Signed-off-by: Helmut Schaa &lt;helmut.schaa@googlemail.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
