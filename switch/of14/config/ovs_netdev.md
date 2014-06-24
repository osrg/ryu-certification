---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
beb2db6c-955e-4e40-a927-a1cd530afddb
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : afbe4e19-6d15-4be7-981c-137877234bd5
controller          : [01e578d7-d283-4840-b418-03c93af389dc]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2ec895a5-43fc-4d40-8998-cf516dd88466, 7623be2f-36bd-498b-bdd6-da6aeeee255c, a02bf31d-2e63-49a7-946f-fd84d1d72b4e, f107fac8-c901-484e-827b-86e69c8b2a0f]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 01e578d7-d283-4840-b418-03c93af389dc
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=1002, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f107fac8-c901-484e-827b-86e69c8b2a0f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2d286a97-7f13-455f-8fce-8702dac89867]
name                : br0

_uuid               : 2ec895a5-43fc-4d40-8998-cf516dd88466
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [327a886c-63cb-47cf-9512-f00b9dffc9fa]
name                : eth21

_uuid               : a02bf31d-2e63-49a7-946f-fd84d1d72b4e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f62c0f7e-dc35-47fc-8e26-c0c34d33869e]
name                : eth23

_uuid               : 7623be2f-36bd-498b-bdd6-da6aeeee255c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c1576b01-3398-4fc8-8686-32e37e572b9d]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 327a886c-63cb-47cf-9512-f00b9dffc9fa
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
statistics          : {collisions=0, rx_bytes=543750313, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=89243097, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c1576b01-3398-4fc8-8686-32e37e572b9d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1195929792, tx_dropped=0, tx_errors=0, tx_packets=35202561}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f62c0f7e-dc35-47fc-8e26-c0c34d33869e
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=3365312080, tx_dropped=0, tx_errors=0, tx_packets=10834160}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2d286a97-7f13-455f-8fce-8702dac89867
admin_state         : down
duplex              : full
ifindex             : 629
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
commit c354fcc575718928224612f135b231f7e1584c2a
Author:     Thomas Graf &lt;tgraf@noironetworks.com&gt;
AuthorDate: Fri Jun 20 13:17:36 2014 +0200
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Jun 24 08:51:17 2014 -0700

    ovs-ofctl.8: Move mod-table out of group tables section
    
    Signed-off-by: Thomas Graf &lt;tgraf@noironetworks.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
