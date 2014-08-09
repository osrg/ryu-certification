---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
313c18b1-2bd9-47c0-803f-b6139ad35f89
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
_uuid               : c3f7a5bc-8e45-44f2-9fbe-578cf67bf11f
controller          : [96cfbef5-7fd5-47f1-8401-81a1c52a740b]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [186bd1a0-11dc-4075-9ed4-e99e15394caa, 5dfe23b5-eb0d-4b58-ab6c-08e27f8bc301, bedc9a15-fe97-418b-be14-d68d5ecd98fc, c5a4a111-81ab-4d41-a54a-28cba7c2d21f]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 96cfbef5-7fd5-47f1-8401-81a1c52a740b
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=661, sec_since_disconnect=7, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 186bd1a0-11dc-4075-9ed4-e99e15394caa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [426a5ada-74a7-4c09-a717-ef8f34009bf1]
name                : eth23

_uuid               : 5dfe23b5-eb0d-4b58-ab6c-08e27f8bc301
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [65b2f750-50ed-4c22-937a-0c1971ff2c24]
name                : eth22

_uuid               : c5a4a111-81ab-4d41-a54a-28cba7c2d21f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2d0e9ec2-2d78-4b46-942f-c53e4e1b9d7a]
name                : eth21

_uuid               : bedc9a15-fe97-418b-be14-d68d5ecd98fc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aad1faf6-53b7-4867-9620-9a7c4dbfc00c]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 65b2f750-50ed-4c22-937a-0c1971ff2c24
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1638748602, tx_dropped=0, tx_errors=0, tx_packets=49784337}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 426a5ada-74a7-4c09-a717-ef8f34009bf1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3690348000, tx_dropped=0, tx_errors=0, tx_packets=2460232}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : aad1faf6-53b7-4867-9620-9a7c4dbfc00c
admin_state         : down
duplex              : full
ifindex             : 98
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

_uuid               : 2d0e9ec2-2d78-4b46-942f-c53e4e1b9d7a
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
statistics          : {collisions=0, rx_bytes=3242635913, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=85232972, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f3ccd17db38d7f574fa26c1615c96b6b207c19df
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Thu Aug 7 21:26:35 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Fri Aug 8 15:52:55 2014 -0700

    datapath: Avoid NULL mask check while building mask
    
    OVS does mask validation even if it does not need to convert
    netlink mask attributes to mask structure.  ovs_nla_get_match&#40;&#41;
    caller can pass NULL mask structure pointer if the caller does
    not need mask.  Therefore NULL check is required in SW_FLOW_KEY*
    macros.  Following patch does not convert mask netlink attributes
    if mask pointer is NULL, so we do not need these checks in
    SW_FLOW_KEY* macro.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
