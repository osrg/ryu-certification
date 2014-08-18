---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
74ab7520-dbb6-4ef3-a90f-e6acc4121a21
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c8719156-dcc2-46b7-a71e-29d2aa064183
controller          : [3d6a5c20-402e-47a5-aa88-b9e1a3383cf6]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [367322fc-5091-4d88-a847-1229b3adb94b, 4a6e9b2e-ca94-4297-a7c5-6ebf52803dab, 758b160d-0d81-427a-8186-e58fce475db0, bab815a0-54eb-45d8-80ad-a02f00d2bb73]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3d6a5c20-402e-47a5-aa88-b9e1a3383cf6
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=682, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 367322fc-5091-4d88-a847-1229b3adb94b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [49a5b1cb-a9b7-40e1-8bb0-3b36abe11a5e]
name                : eth23

_uuid               : bab815a0-54eb-45d8-80ad-a02f00d2bb73
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aaf19ac7-96a4-403d-8489-80e8f5104a72]
name                : eth21

_uuid               : 758b160d-0d81-427a-8186-e58fce475db0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [542af099-ce49-4533-bd0a-3b36001e1d85]
name                : br0

_uuid               : 4a6e9b2e-ca94-4297-a7c5-6ebf52803dab
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1cbffbc9-aae3-4525-af8f-fd619e882e41]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 542af099-ce49-4533-bd0a-3b36001e1d85
admin_state         : down
duplex              : full
ifindex             : 30
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

_uuid               : 1cbffbc9-aae3-4525-af8f-fd619e882e41
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=104237886, tx_dropped=0, tx_errors=0, tx_packets=69978}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 49a5b1cb-a9b7-40e1-8bb0-3b36abe11a5e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=162274500, tx_dropped=0, tx_errors=0, tx_packets=108183}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : aaf19ac7-96a4-403d-8489-80e8f5104a72
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
statistics          : {collisions=0, rx_bytes=222113338, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=149107, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6ce798bd708d3406fe3ab0e1452a37f8cd7f8cdc
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Mon Aug 18 07:41:34 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Mon Aug 18 10:23:40 2014 -0700

    netinet/in.h: Add definition for IPPROTO_GRE.
    
    Commit b7ea2d480338&#40;Extend OVS IPFIX exporter to export tunnel headers&#41;
    added a usage for IPROTO_GRE. But that does not look available in any
    Visual Studio headers. So add it.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
