---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e59833e2-85b3-4cd0-b162-2d2a7c4740c5
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 81526aa2-0e41-48da-bcbe-03f54b5f6706
controller          : [cbe21b4c-445f-4402-96bb-8f878a69b311]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0779ea20-1303-43b0-bc63-d985a9909651, 204a9b28-89a4-4133-9cdf-055db00489c8, 6b44ba98-823e-47b9-9b85-566d6a342adb, afd54d40-a718-4187-bc85-028424e31190]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : cbe21b4c-445f-4402-96bb-8f878a69b311
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=972, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 204a9b28-89a4-4133-9cdf-055db00489c8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c9ea3033-5419-4b0c-9689-7c17ff922cef]
name                : eth21

_uuid               : 0779ea20-1303-43b0-bc63-d985a9909651
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b6c5a068-2f49-4c38-b475-da5301eef07c]
name                : eth23

_uuid               : afd54d40-a718-4187-bc85-028424e31190
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e5938d05-fdfa-4c0c-bbe2-98f622757920]
name                : eth22

_uuid               : 6b44ba98-823e-47b9-9b85-566d6a342adb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e61bbd2c-84c6-4aff-8774-bdb0a464bedb]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b6c5a068-2f49-4c38-b475-da5301eef07c
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=921469284, tx_dropped=0, tx_errors=0, tx_packets=12068243}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e61bbd2c-84c6-4aff-8774-bdb0a464bedb
admin_state         : down
ifindex             : 680
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

_uuid               : e5938d05-fdfa-4c0c-bbe2-98f622757920
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1974777872, tx_dropped=0, tx_errors=0, tx_packets=35726178}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c9ea3033-5419-4b0c-9689-7c17ff922cef
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
statistics          : {collisions=0, rx_bytes=2753305584, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=90727912, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 210ba964f5c6ed0a4696fd16344475a31c313823
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Mon Jun 23 05:33:56 2014 +0000
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Wed Jun 25 18:05:19 2014 +1200

    tests: Remove extraneous parenthesis from test name.
    
    This could cause configuration failure on earlier versions of autoconf.
    
    Reported-by: Lin Shaopeng &lt;slin0209@gmail.com&gt;
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
