---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ad0971e4-f1bc-4eb9-918d-ec2ff72d4601
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f2fd29d2-51fe-4042-bfeb-4ee1bdd6144c
controller          : [0d9f42a0-f1e5-41ed-85f9-e949159fd375]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [18030bee-d181-405a-88b0-d3601e3386bf, 5a799d59-a86a-4132-bfdb-80fe3c8ea1fc, 61c67298-8263-4bf8-b47e-9b06d674d6ae, 8ca9480e-ce2c-4b62-a34a-2bc112cc1c24]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0d9f42a0-f1e5-41ed-85f9-e949159fd375
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=977, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 61c67298-8263-4bf8-b47e-9b06d674d6ae
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bc80249e-6fff-415a-980a-73cd78cbb853]
name                : eth23

_uuid               : 5a799d59-a86a-4132-bfdb-80fe3c8ea1fc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a488457d-15bf-41ed-862b-e366d1678cc8]
name                : br0

_uuid               : 8ca9480e-ce2c-4b62-a34a-2bc112cc1c24
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e095a4b5-3ee6-4ca3-a809-ebda68a4c761]
name                : eth21

_uuid               : 18030bee-d181-405a-88b0-d3601e3386bf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0d4727a5-7ebf-4738-919e-1afe3de4c811]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e095a4b5-3ee6-4ca3-a809-ebda68a4c761
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
statistics          : {collisions=0, rx_bytes=1584230624, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=89942222, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a488457d-15bf-41ed-862b-e366d1678cc8
admin_state         : down
duplex              : full
ifindex             : 660
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

_uuid               : 0d4727a5-7ebf-4738-919e-1afe3de4c811
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1566099532, tx_dropped=0, tx_errors=0, tx_packets=35451408}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : bc80249e-6fff-415a-980a-73cd78cbb853
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=4222467580, tx_dropped=0, tx_errors=0, tx_packets=11405597}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ccf4378615e93618e6ab8423fa1400b40876df91
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Tue Jun 24 20:56:57 2014 +0900
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Tue Jun 24 16:02:02 2014 -0700

    datapath: Add basic MPLS support to kernel
    
    Allow datapath to recognize and extract MPLS labels into flow keys
    and execute actions which push, pop, and set labels on packets.
    
    Based heavily on work by Leo Alterman, Ravi K, Isaku Yamahata and Joe Stringer.
    
    Cc: Ravi K &lt;rkerur@gmail.com&gt;
    Cc: Leo Alterman &lt;lalterman@nicira.com&gt;
    Cc: Isaku Yamahata &lt;yamahata@valinux.co.jp&gt;
    Cc: Joe Stringer &lt;joe@wand.net.nz&gt;
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
