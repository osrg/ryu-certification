---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fbf847d6-5032-4ba0-a6f2-8f87de274ea5
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
_uuid               : 8964d719-d609-422a-9dcc-4276b27a3e2e
controller          : [9c50da5d-b006-4315-8ed2-c2c2282baa12]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4ea70d31-1ae9-4b6d-a6eb-334ecb646caa, 5ba7eee0-cfa1-4903-89c1-202602301f7d, a0d32e0e-3a1f-4192-b04c-fb050fb076ba]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9c50da5d-b006-4315-8ed2-c2c2282baa12
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5ba7eee0-cfa1-4903-89c1-202602301f7d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [80259318-a874-4139-bb27-3795c512ea50]
name                : eth7

_uuid               : 4ea70d31-1ae9-4b6d-a6eb-334ecb646caa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7f729669-b7fd-46e8-9400-96a6026ec7dc]
name                : eth8

_uuid               : a0d32e0e-3a1f-4192-b04c-fb050fb076ba
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3057cd8a-e189-4a5e-9901-a155cc5e4959]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 80259318-a874-4139-bb27-3795c512ea50
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
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 7f729669-b7fd-46e8-9400-96a6026ec7dc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 3057cd8a-e189-4a5e-9901-a155cc5e4959
admin_state         : up
ifindex             : 83
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6a4d3ab53d53bc97ab9eee8709c5720dea1fb260
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed Jan 15 10:22:20 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jan 16 12:27:03 2014 -0800

    ofproto-dpif: Add more lock annotations.
    
    This annotation would have caught the bug fixed by commit 491a67a0005347130
    (ofproto-dpif-xlate: Avoid recursive acquisition of xlate_rwlock.).
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    CC: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
</pre>
