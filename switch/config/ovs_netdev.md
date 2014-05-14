---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
01da58d5-7960-4d01-97d2-48bbbf2f7b14
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
_uuid               : a90fc493-3a73-4517-a561-bf8d4d5742bf
controller          : [715e4ebf-80d6-4423-8c67-ea6fed5cfd94]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [011ecad8-2be9-4acc-b2ef-b5bef8ca20a8, 08a9b85e-d006-4af2-b2b7-aea8b8251ce9, 8284fd01-bf32-40e8-91c3-108b3cf55ce0, 9eb34a19-e6e2-4911-a8f2-e8e926ae5ad1]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 715e4ebf-80d6-4423-8c67-ea6fed5cfd94
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=551, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 011ecad8-2be9-4acc-b2ef-b5bef8ca20a8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c5f3d71c-6c08-42d9-aef4-46dcf7c2f5b9]
name                : eth21

_uuid               : 8284fd01-bf32-40e8-91c3-108b3cf55ce0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [999d8989-8fd4-435a-a5c7-1b3336035716]
name                : eth22

_uuid               : 9eb34a19-e6e2-4911-a8f2-e8e926ae5ad1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7aeaf90d-34a8-4f16-8519-da3fe4ec5322]
name                : br0

_uuid               : 08a9b85e-d006-4af2-b2b7-aea8b8251ce9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [73d0b248-f736-4ecf-8d3c-2835b6210b7b]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c5f3d71c-6c08-42d9-aef4-46dcf7c2f5b9
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
statistics          : {collisions=0, rx_bytes=2767188974, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1858122, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 73d0b248-f736-4ecf-8d3c-2835b6210b7b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1802566500, tx_dropped=0, tx_errors=0, tx_packets=1201711}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 999d8989-8fd4-435a-a5c7-1b3336035716
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1190154084, tx_dropped=0, tx_errors=0, tx_packets=798363}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 7aeaf90d-34a8-4f16-8519-da3fe4ec5322
admin_state         : down
duplex              : full
ifindex             : 162
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 226cb5bf14e5df6c5b427715b605635890907cd0
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed May 14 10:25:11 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed May 14 10:25:11 2014 -0700

    AUTHORS: Add Ashwin Swaminathan.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
