---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b11f1d36-f06e-4d8c-b1fb-d59229bf1e4e
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 189dde9f-7756-4e3d-955a-3b4b6e35a03e
controller          : [3791eecb-781e-44fd-913f-4aef0072cf41]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [b1a176fa-04fa-4e27-9862-5c4e5b067825, ce66cc24-f910-4748-b8d8-2470307a314b, dcba686b-5d5d-424a-837a-f2fb7f6c0379, e0c8dd80-d4cc-430b-820a-405743b7b332]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3791eecb-781e-44fd-913f-4aef0072cf41
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=666, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e0c8dd80-d4cc-430b-820a-405743b7b332
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [124fd0bb-96ac-4716-bf8b-8c8a2e9adb75]
name                : eth23

_uuid               : ce66cc24-f910-4748-b8d8-2470307a314b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b4a148a3-45bd-408f-868e-5eb23e9b22bb]
name                : eth22

_uuid               : b1a176fa-04fa-4e27-9862-5c4e5b067825
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [233bf8a9-0140-4a4a-b490-6e147172ef87]
name                : br0

_uuid               : dcba686b-5d5d-424a-837a-f2fb7f6c0379
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d4dd31a4-5e02-4205-8fa0-64b6d76a5cca]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d4dd31a4-5e02-4205-8fa0-64b6d76a5cca
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
statistics          : {collisions=0, rx_bytes=1542983689, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=75532429, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 233bf8a9-0140-4a4a-b490-6e147172ef87
admin_state         : down
duplex              : full
ifindex             : 186
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

_uuid               : b4a148a3-45bd-408f-868e-5eb23e9b22bb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2886830342, tx_dropped=0, tx_errors=0, tx_packets=47763679}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 124fd0bb-96ac-4716-bf8b-8c8a2e9adb75
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3466106204, tx_dropped=0, tx_errors=0, tx_packets=5174049}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ddc3b06d348793ae3f858a832ce5c9053d7a621b
Author:     Justin Pettit &lt;jpettit@nicira.com&gt;
AuthorDate: Mon Sep 29 11:15:12 2014 -0700
Commit:     Justin Pettit &lt;jpettit@nicira.com&gt;
CommitDate: Mon Sep 29 12:57:58 2014 -0700

    FAQ: Replace reference to OVS 2.2 with 2.3.
    
    We never released 2.2.0, so references to it are confusing.
    
    Signed-off-by: Justin Pettit &lt;jpettit@nicira.com&gt;
    Acked-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
