---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
be7213bd-e852-43a2-aca2-db30097dedb4
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 2dda680e-28f0-4502-b3b6-3c9ce5ce1392
controller          : [91ad825c-7e8c-47d2-8181-606fdf8e92b3]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [59df216f-f52f-473a-a752-9f786e575090, 9f156811-d413-4f38-9e83-8865a08a6369, b023c804-9bfd-47d7-9888-344bd4401db6, b4446377-c301-4017-899e-fa9d6f69c946]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 91ad825c-7e8c-47d2-8181-606fdf8e92b3
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=552, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b023c804-9bfd-47d7-9888-344bd4401db6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [07c22df0-87ce-4ee6-8f82-3d213a55e766]
name                : eth21

_uuid               : 9f156811-d413-4f38-9e83-8865a08a6369
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [67878c65-e34e-4a8b-8ee6-0a4d80b4cf69]
name                : eth23

_uuid               : b4446377-c301-4017-899e-fa9d6f69c946
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1cc255a6-1061-4a2b-a93f-1a7f3162bce1]
name                : eth22

_uuid               : 59df216f-f52f-473a-a752-9f786e575090
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c2ffa87a-0f9c-4f02-b229-0317a7ebae27]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 07c22df0-87ce-4ee6-8f82-3d213a55e766
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
statistics          : {collisions=0, rx_bytes=75893279, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2928022, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 67878c65-e34e-4a8b-8ee6-0a4d80b4cf69
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3071007000, tx_dropped=0, tx_errors=0, tx_packets=2047338}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c2ffa87a-0f9c-4f02-b229-0317a7ebae27
admin_state         : down
duplex              : full
ifindex             : 157
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

_uuid               : 1cc255a6-1061-4a2b-a93f-1a7f3162bce1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1766920050, tx_dropped=0, tx_errors=0, tx_packets=1183250}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6814c630e45b03186c12525048c8fde34219bc48
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Wed May 21 19:04:44 2014 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Wed May 21 21:09:15 2014 -0700

    FAQ: Add a list of upstream kernel version supporting tunneling.
    
    Reported-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
