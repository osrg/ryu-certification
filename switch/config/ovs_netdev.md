---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
025f7e2f-0801-4210-b5c5-d09370f1b9df
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 4538bcfa-2c22-44d4-bfd4-15e8bbe73c2e
controller          : [1aeea505-785b-484c-8a17-1bb6e64735b7]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [41e29067-2f82-4950-9952-b6b90040ed49, 87baa234-8f6a-412a-bcad-15396cd15576, ddffc53a-b9f7-4e91-ad28-19b7c2569998]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 1aeea505-785b-484c-8a17-1bb6e64735b7
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=297, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 87baa234-8f6a-412a-bcad-15396cd15576
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d1765793-2858-41ab-b55b-b582a413a536]
name                : eth7

_uuid               : ddffc53a-b9f7-4e91-ad28-19b7c2569998
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6c0a2bea-b0a6-4c42-9a42-b4fa18e29f89]
name                : br0

_uuid               : 41e29067-2f82-4950-9952-b6b90040ed49
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [67a7334a-9da9-424c-9be9-e37a5f5cbd02]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 67a7334a-9da9-424c-9be9-e37a5f5cbd02
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=970638, tx_dropped=0, tx_errors=0, tx_packets=10376}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 6c0a2bea-b0a6-4c42-9a42-b4fa18e29f89
admin_state         : up
duplex              : full
ifindex             : 139
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

_uuid               : d1765793-2858-41ab-b55b-b582a413a536
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
statistics          : {collisions=0, rx_bytes=3054430711, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72545879, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0a0857df473cad7e8ce610f10813c94569953f98
Author:     Joe Perches &lt;joe@perches.com&gt;
AuthorDate: Mon Feb 3 17:27:41 2014 -0800
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Mon Feb 3 17:27:41 2014 -0800

    datapath: flow_netlink: Use pr_fmt to OVS_NLERR
    
    Add openvswitch:  prefix to OVS_NLERR output
    to match the other OVS_NLERR output of datapath.c
    
    Signed-off-by: Joe Perches &lt;joe@perches.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
