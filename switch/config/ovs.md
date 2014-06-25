---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
80ea7791-e02c-473b-9ded-4e561c70b600
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
_uuid               : ea253de4-6b16-4c53-b5c7-35af2caa68bc
controller          : [0116faca-bf68-4fed-8c33-160ba57b8efc]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [07914d92-8470-404f-952e-5bee56435f7f, 4d567718-849b-476a-8dd6-04a7f7db1194, 88509c7a-0f5f-4fbf-9b33-7fa382ec3c3b, c342b13a-4db6-42b5-ae14-7aacf10af4ab]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0116faca-bf68-4fed-8c33-160ba57b8efc
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=976, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4d567718-849b-476a-8dd6-04a7f7db1194
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ffddad0c-5d8e-4230-98b7-87628f475890]
name                : eth23

_uuid               : 07914d92-8470-404f-952e-5bee56435f7f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [569c0697-42e9-4c1e-ad48-e75037cdcc76]
name                : eth21

_uuid               : c342b13a-4db6-42b5-ae14-7aacf10af4ab
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [26470292-9760-40a6-a4a3-c2ad1bb1c8a3]
name                : br0

_uuid               : 88509c7a-0f5f-4fbf-9b33-7fa382ec3c3b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [20f6d483-b01b-4970-a9c8-269a7fdfd03f]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ffddad0c-5d8e-4230-98b7-87628f475890
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=1716446784, tx_dropped=0, tx_errors=0, tx_packets=12598228}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 26470292-9760-40a6-a4a3-c2ad1bb1c8a3
admin_state         : down
ifindex             : 696
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 20f6d483-b01b-4970-a9c8-269a7fdfd03f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2301926044, tx_dropped=0, tx_errors=0, tx_packets=35946131}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 569c0697-42e9-4c1e-ad48-e75037cdcc76
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
statistics          : {collisions=0, rx_bytes=3688568552, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=91356466, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e381def9712019bfb667605c1f3dba5ce2266c44
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Tue Jun 24 13:00:52 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Wed Jun 25 09:28:42 2014 -0700

    lib: Rename ofp to buf.
    
    dpif-packet contains ofpbuf which points to packet data.  Here buf
    is better name rather than ofp.
    Following patch renames all remaining instances of ofp variable.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
</pre>
