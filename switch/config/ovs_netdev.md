---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
36c9c63e-c6b6-48b9-b149-0e987b92b627
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 61d9948b-52b3-4761-bf0d-d0cf62fa468e
controller          : [3fd85fc5-3b1d-46f9-9659-396f68c0de78]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [3a50772f-f2d3-4f83-ad9f-e1d2214bebb3, 3b36b8df-c8ba-4a86-be7d-2f6eb10519a1, 9f73260c-ef9a-4c7c-963b-61e6f4146154, d5607969-a808-4e18-93d1-a3b4649c52b5]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3fd85fc5-3b1d-46f9-9659-396f68c0de78
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=692, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9f73260c-ef9a-4c7c-963b-61e6f4146154
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9d4ff9a2-758a-4437-9230-32f021896027]
name                : eth22

_uuid               : d5607969-a808-4e18-93d1-a3b4649c52b5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ad0cbf2f-1a68-4150-ac0e-dde3cc51936b]
name                : br0

_uuid               : 3b36b8df-c8ba-4a86-be7d-2f6eb10519a1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [010dadb3-2837-42b5-88e4-c8dbddce5bec]
name                : eth23

_uuid               : 3a50772f-f2d3-4f83-ad9f-e1d2214bebb3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [69ebf581-8d56-4d73-b611-b30213f594ab]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 69ebf581-8d56-4d73-b611-b30213f594ab
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
statistics          : {collisions=0, rx_bytes=2134163661, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=170451543, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9d4ff9a2-758a-4437-9230-32f021896027
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2413667212, tx_dropped=0, tx_errors=0, tx_packets=104730388}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ad0cbf2f-1a68-4150-ac0e-dde3cc51936b
admin_state         : down
duplex              : full
ifindex             : 273
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

_uuid               : 010dadb3-2837-42b5-88e4-c8dbddce5bec
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3475864408, tx_dropped=0, tx_errors=0, tx_packets=8043866}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 2c26eabfb71cc8de7b5f84570e18e2816e867df1
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Tue Oct 21 16:10:38 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Oct 22 09:01:42 2014 -0700

    netlink-socket: Use poll_immediate_wake&#40;&#41; on Windows.
    
    We have not yet tested the wakup via pending IRP functionality on
    Windows yet. Hence we use poll_immediate_wake&#40;&#41;.
    
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Eitan Eliahu &lt;eliahue@vmware.com&gt;
</pre>
