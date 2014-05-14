---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
05aa8f3b-73e2-4bbb-bebe-39969c4de65b
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 28f10d4c-175f-45b2-9b5a-8d158425d911
controller          : [ad0ee919-d685-445d-a2f1-28ef3630bc3c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [569c9d97-cf89-43ae-ac5f-964dccf4d213, 96d766a2-1852-4dae-89d0-12e39431c623, f433a54d-ef39-4c21-8e7b-f2b59eda3378, f6ce83f6-7c2f-4e7c-977b-81ec9ec64c90]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ad0ee919-d685-445d-a2f1-28ef3630bc3c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=552, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f433a54d-ef39-4c21-8e7b-f2b59eda3378
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3ab21115-cbf4-4678-aab0-5d8ab2a8a910]
name                : eth23

_uuid               : 96d766a2-1852-4dae-89d0-12e39431c623
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [076f89dc-e412-4305-9295-566766e7dfb6]
name                : eth22

_uuid               : f6ce83f6-7c2f-4e7c-977b-81ec9ec64c90
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4b47af01-c430-4198-ac30-6daf5f030552]
name                : eth21

_uuid               : 569c9d97-cf89-43ae-ac5f-964dccf4d213
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c9bf8ba9-9082-4ad4-89c1-4c12abc1d398]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 076f89dc-e412-4305-9295-566766e7dfb6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1251458926, tx_dropped=0, tx_errors=0, tx_packets=839460}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3ab21115-cbf4-4678-aab0-5d8ab2a8a910
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1951681500, tx_dropped=0, tx_errors=0, tx_packets=1301121}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 4b47af01-c430-4198-ac30-6daf5f030552
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
statistics          : {collisions=0, rx_bytes=2954245540, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1983453, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c9bf8ba9-9082-4ad4-89c1-4c12abc1d398
admin_state         : down
duplex              : full
ifindex             : 168
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
commit 52ca734e820d6b183aba5ca1c7d714f3c7e7a781
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed May 14 10:33:35 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed May 14 10:33:35 2014 -0700

    meta-flow: Use OXM-defined constant for TCP flags in OpenFlow 1.5.
    
    This also adds the definitions of a few other OXM headers we didn't have
    yet.
    
    EXT-109.
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
