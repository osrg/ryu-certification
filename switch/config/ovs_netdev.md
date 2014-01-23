---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1acc607c-0537-4f10-b648-6420642bf678
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f456c08b-7af5-44e3-a2db-c3df10a3d34f
controller          : [cf87d4ad-3919-4630-8eb7-8f37a198398a]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [b64dabbc-dec4-43fc-a8d9-79b950764543, c87c7985-aa77-44bf-9c30-b52aa2a67b45, d391323e-bb16-4158-8f96-db5988c23906]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : cf87d4ad-3919-4630-8eb7-8f37a198398a
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=242, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b64dabbc-dec4-43fc-a8d9-79b950764543
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a5a16829-c68b-4edf-ab17-6a11237b7e71]
name                : eth7

_uuid               : c87c7985-aa77-44bf-9c30-b52aa2a67b45
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e7f12711-46de-4a94-8499-60ce21d9d3b4]
name                : br0

_uuid               : d391323e-bb16-4158-8f96-db5988c23906
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [77a387a5-4e50-473a-a69c-368e0e1b2bc2]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 77a387a5-4e50-473a-a69c-368e0e1b2bc2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=98778, tx_dropped=0, tx_errors=0, tx_packets=1050}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : e7f12711-46de-4a94-8499-60ce21d9d3b4
admin_state         : up
duplex              : full
ifindex             : 42
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

_uuid               : a5a16829-c68b-4edf-ab17-6a11237b7e71
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
statistics          : {collisions=0, rx_bytes=374996, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=3767, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d15ae707727d8766f3bfa58f3923330ed078a636
Author:     Daniele Di Proietto &lt;daniele.di.proietto@gmail.com&gt;
AuthorDate: Thu Jan 23 17:19:29 2014 +0100
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Thu Jan 23 10:42:41 2014 -0800

    datapath: use const in some local vars and casts
    
    In few functions, const formal parameters are assigned or cast to
    non-const.
    These changes suppress warnings if compiled with -Wcast-qual.
    
    Signed-off-by: Daniele Di Proietto &lt;daniele.di.proietto@gmail.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
