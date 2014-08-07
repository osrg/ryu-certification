---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7ba375b9-a0c6-43be-b15c-a55df0d474fe
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c5237725-7ecf-48f1-b52d-40c1a7fae0c1
controller          : [a89dbe74-7240-4bb1-adb6-57513f1f010f]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [35cdba2b-7c31-4813-96bb-3287a6835fa4, b246cf24-8c81-4964-8a8d-9383f9ee0434, c311fccd-a241-4551-8bcc-3a8eebc32ba2, cf5c05ee-206c-4263-8cfa-7af08d93a38d]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a89dbe74-7240-4bb1-adb6-57513f1f010f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=677, sec_since_disconnect=6, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b246cf24-8c81-4964-8a8d-9383f9ee0434
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1f08c9c9-5bf9-4c83-aef8-c9cffb26bcc9]
name                : eth21

_uuid               : c311fccd-a241-4551-8bcc-3a8eebc32ba2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [90475129-d04d-4e6f-b3cd-114ee36fa8c5]
name                : br0

_uuid               : cf5c05ee-206c-4263-8cfa-7af08d93a38d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2ae96a65-3dff-4e38-a06b-06db2657b3bf]
name                : eth23

_uuid               : 35cdba2b-7c31-4813-96bb-3287a6835fa4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [364b44a8-05b2-4052-a7ef-7dec06daf98a]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 364b44a8-05b2-4052-a7ef-7dec06daf98a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1393230988, tx_dropped=0, tx_errors=0, tx_packets=49618708}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 90475129-d04d-4e6f-b3cd-114ee36fa8c5
admin_state         : down
ifindex             : 85
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

_uuid               : 2ae96a65-3dff-4e38-a06b-06db2657b3bf
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3094519500, tx_dropped=0, tx_errors=0, tx_packets=2063013}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 1f08c9c9-5bf9-4c83-aef8-c9cffb26bcc9
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
statistics          : {collisions=0, rx_bytes=2541437535, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=84761319, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fb66fbd15b98e897841f326b6dd0842ba6bde1a9
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Tue Aug 5 13:49:57 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Wed Aug 6 22:12:25 2014 -0700

    datapath: Use tun_info only for egress tunnel path.
    
    Currently tun_info is used for passing tunnel information
    on ingress and egress path, this cause confusion.  Following
    patch removes its use on ingress path make it egress only parameter.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
