---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6791e43f-65c7-436b-b244-c269dbba5b57
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b5e884f2-9783-4c7e-8386-a9e64d5af89f
controller          : [e8b1366e-ce6c-444b-8758-319f0c1e616c]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [58e470e6-fc70-4147-97e5-086e6f518b25, d1422988-2343-493e-8007-1d80349a5d97, faabb28c-55d1-45e9-a5b3-3de2cc6ae327]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e8b1366e-ce6c-444b-8758-319f0c1e616c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d1422988-2343-493e-8007-1d80349a5d97
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9d456a88-ddb0-4acf-bdbd-f2d1944e1dc3]
name                : eth8

_uuid               : faabb28c-55d1-45e9-a5b3-3de2cc6ae327
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ff2c2fa5-4c69-49ec-8b14-3966dde56e55]
name                : eth7

_uuid               : 58e470e6-fc70-4147-97e5-086e6f518b25
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [321acad1-afd5-429d-b4d5-63b78d58a9c3]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9d456a88-ddb0-4acf-bdbd-f2d1944e1dc3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : ff2c2fa5-4c69-49ec-8b14-3966dde56e55
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
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 321acad1-afd5-429d-b4d5-63b78d58a9c3
admin_state         : up
ifindex             : 105
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal
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
