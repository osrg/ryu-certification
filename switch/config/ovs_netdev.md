---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8b1f521d-838c-4329-8ad0-ceb003fffe92
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b7af8fae-d82d-49bb-a330-d201704ea9ab
controller          : [bab209c8-36e3-46d2-b373-ba850e11285a]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [18aa90ae-276c-4a40-b5e4-d80ffef264cc, 3f6c9a8c-6bb7-4db8-9912-8a9c30222e0f, 53aeec7d-82ee-4114-b9d8-38d457a7cd23]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : bab209c8-36e3-46d2-b373-ba850e11285a
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=377, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3f6c9a8c-6bb7-4db8-9912-8a9c30222e0f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e7b1a899-fb8b-49ea-a232-1d37c8f2b907]
name                : eth8

_uuid               : 53aeec7d-82ee-4114-b9d8-38d457a7cd23
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e8aa3f38-f5ef-4510-bd83-1dd0809bcb0b]
name                : br0

_uuid               : 18aa90ae-276c-4a40-b5e4-d80ffef264cc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c3d16b74-59da-4d5b-8228-586426cb18ce]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e8aa3f38-f5ef-4510-bd83-1dd0809bcb0b
admin_state         : up
duplex              : full
ifindex             : 332
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

_uuid               : c3d16b74-59da-4d5b-8228-586426cb18ce
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
statistics          : {collisions=0, rx_bytes=3059646373, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72598534, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : e7b1a899-fb8b-49ea-a232-1d37c8f2b907
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2651686, tx_dropped=0, tx_errors=0, tx_packets=28307}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 71c24bb0f881fde3304de61e19bb4e0c5512da30
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Fri Feb 21 14:03:51 2014 -0800
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Fri Feb 21 14:07:46 2014 -0800

    dpif-netdev: Fix memory leak.
    
    In dpif_netdev_flow_del() and dp_netdev_port_input(), the
    referenced 'netdev_flow' is not un-referenced.  This causes
    the leak of the struct's memory.
    
    This commit fixes the above issue by calling dp_netdev_flow_unref()
    after using the reference.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
