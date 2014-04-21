---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3555bfd2-2cc9-4dc1-8346-c33c1fd4f184
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
_uuid               : a728dcee-8619-4f1e-b620-580e890d08bd
controller          : [83e6d7f5-d3c2-4e76-b4f9-2ed6b533c856]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [013c4ebe-6413-4fe6-9905-3e6d818fba6e, 329fef03-0912-42c1-888a-29a37b8237d1, 6b634d7e-de99-458d-8516-f3aa077f8aac, cba3ba0e-e8e9-43d5-a8e0-39c85fc1ee62]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 83e6d7f5-d3c2-4e76-b4f9-2ed6b533c856
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=572, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6b634d7e-de99-458d-8516-f3aa077f8aac
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6ab73e57-6f86-46e2-8904-978984ff46b0]
name                : br0

_uuid               : 013c4ebe-6413-4fe6-9905-3e6d818fba6e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [23d3fd24-3618-4c54-9c18-91ebe0a3e59d]
name                : eth23

_uuid               : cba3ba0e-e8e9-43d5-a8e0-39c85fc1ee62
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c028f6b8-6de0-4133-b7ce-f4fe4f6df68f]
name                : eth21

_uuid               : 329fef03-0912-42c1-888a-29a37b8237d1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0990288b-6c6d-4cfe-bf72-5d23a5d826bb]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 23d3fd24-3618-4c54-9c18-91ebe0a3e59d
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1500
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=218496000, tx_dropped=0, tx_errors=0, tx_packets=145664}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c028f6b8-6de0-4133-b7ce-f4fe4f6df68f
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=421405325, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=284898, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6ab73e57-6f86-46e2-8904-978984ff46b0
admin_state         : down
duplex              : full
ifindex             : 1060
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

_uuid               : 0990288b-6c6d-4cfe-bf72-5d23a5d826bb
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1500
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=272843974, tx_dropped=0, tx_errors=0, tx_packets=183375}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a605908001070c27aa8c755c92cd361a10b46beb
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Tue Apr 8 11:13:42 2014 +0000
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Mon Apr 21 11:06:55 2014 -0700

    datapath: add recirc action
    
    Recirculation implementation for Linux kernel data path.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
