---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a93e1b7a-5e0c-4ad9-bae4-8020f23c8739
    Bridge br0
        Controller tcp:10.24.150.30
            is_connected: true
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b41afb92-f9de-4da7-a460-21b3b9309517
controller          : [cee2cd13-8738-4a4f-b569-9fec7211287c]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [11412735-2d3c-46ef-bb31-f4207bf1926a, 4008fa2f-7097-45d4-aa30-4f976000c1ff, 4588d38f-72c0-4c01-81d4-d9b20bb7744e, e8f84a32-2499-42e2-bc26-07908c5219dc]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : cee2cd13-8738-4a4f-b569-9fec7211287c
is_connected        : true
role                : other
status              : {last_error=Connection refused, sec_since_connect=2, sec_since_disconnect=4, state=ACTIVE}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 11412735-2d3c-46ef-bb31-f4207bf1926a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9df0102a-dc76-4400-892c-45cd4ad1e15a]
name                : eth23

_uuid               : e8f84a32-2499-42e2-bc26-07908c5219dc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1a296164-7aed-4fa1-a5a6-3c24cc609530]
name                : br0

_uuid               : 4008fa2f-7097-45d4-aa30-4f976000c1ff
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8f86d46b-9206-4eeb-981a-7cc8a0075c29]
name                : eth22

_uuid               : 4588d38f-72c0-4c01-81d4-d9b20bb7744e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0a2c85b9-a761-4e6b-95f8-cbce9d7cc858]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1a296164-7aed-4fa1-a5a6-3c24cc609530
admin_state         : down
ifindex             : 1070
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 0a2c85b9-a761-4e6b-95f8-cbce9d7cc858
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9df0102a-dc76-4400-892c-45cd4ad1e15a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8f86d46b-9206-4eeb-981a-7cc8a0075c29
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3aadc5bbb058d52bb350424cbfef80f2d0c50ecd
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Mon Apr 21 20:05:08 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Mon Apr 21 21:14:04 2014 -0700

    ofproto-dpif-upcall: Fix logic error in handler/revalidator threads
    creation and deletion.
    
    Commit 1f8675481e &#40;ofproto-dpif-upcall: Fix ovs-vswitchd crash.&#41;
    directly copied the udpif_set_threads&#40;&#41; logic to udpif_stop_threads&#40;&#41;
    and udpif_start_threads&#40;&#41;.  In fact, this was erroneous and caused
    unittest failures.
    
    This commit fixes the above issue by correcting the checks in
    udpif_stop_threads&#40;&#41; and udpif_start_threads&#40;&#41;, and adding necessary
    checks in udpif_set_threads&#40;&#41;.
    
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
