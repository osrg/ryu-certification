---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
cf72fd0d-f69d-4d43-a0b1-d4952863894b
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0b62d5e1-1ea2-47c9-8985-68e21c134dad
controller          : [83d9f59a-448c-47df-9696-69900a1a3531]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [035d6c3a-3233-46df-9c3f-3832e0a621b8, 3d646f06-647a-41c0-afb6-11134aa50d3d, d5cfe211-c7d3-4b75-8507-5c55909f9191, d72e34f9-f15c-4fe6-9c95-b5c0a76a9a09]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 83d9f59a-448c-47df-9696-69900a1a3531
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=972, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d72e34f9-f15c-4fe6-9c95-b5c0a76a9a09
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b442c0f6-b8df-4b09-b6f9-a06796a69f26]
name                : eth22

_uuid               : d5cfe211-c7d3-4b75-8507-5c55909f9191
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3c41551b-a7f6-4c83-a9e9-faa1405cde6d]
name                : eth21

_uuid               : 3d646f06-647a-41c0-afb6-11134aa50d3d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8be68c60-88d7-4fe4-b0d6-b02a2c5c2d10]
name                : br0

_uuid               : 035d6c3a-3233-46df-9c3f-3832e0a621b8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b8cbef9b-bfe5-42ea-bee9-2ef934ae72de]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8be68c60-88d7-4fe4-b0d6-b02a2c5c2d10
admin_state         : down
duplex              : full
ifindex             : 551
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

_uuid               : b442c0f6-b8df-4b09-b6f9-a06796a69f26
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2050708015, tx_dropped=0, tx_errors=0, tx_packets=21447370}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b8cbef9b-bfe5-42ea-bee9-2ef934ae72de
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=637610080, tx_dropped=0, tx_errors=0, tx_packets=9015692}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3c41551b-a7f6-4c83-a9e9-faa1405cde6d
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
statistics          : {collisions=0, rx_bytes=203472472, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=43180326, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 271e6bc7d27bf19c666a37beeaeeec8017850c44
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Fri Jun 20 17:23:33 2014 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Fri Jun 20 17:23:33 2014 -0700

    doc: Additional documentation updates for Geneve.
    
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
