---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
bef3a897-88fd-4298-9b9f-268ed3aae289
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 25408e64-c2c8-4b34-a7f0-4194882ec7d5
controller          : [35df1ab7-f4c1-40b5-ae87-ff67e7e7988c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [aa755adc-513e-41fe-b82c-2963f2629ced, c175759a-85b8-4b7e-a8d6-43daf2a6c9ca, fad92abf-43de-4c05-853c-8aa8584eec88]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 35df1ab7-f4c1-40b5-ae87-ff67e7e7988c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=301, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : aa755adc-513e-41fe-b82c-2963f2629ced
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f6e355e3-e7e5-4f6c-858f-2af82919e5be]
name                : br0

_uuid               : c175759a-85b8-4b7e-a8d6-43daf2a6c9ca
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ab964253-a91d-4bcf-a4dc-4570fb71e503]
name                : eth8

_uuid               : fad92abf-43de-4c05-853c-8aa8584eec88
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6bbb79ee-871f-4910-972c-2a3f0d086202]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6bbb79ee-871f-4910-972c-2a3f0d086202
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
statistics          : {collisions=0, rx_bytes=3054104297, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72542578, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : f6e355e3-e7e5-4f6c-858f-2af82919e5be
admin_state         : up
duplex              : full
ifindex             : 128
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

_uuid               : ab964253-a91d-4bcf-a4dc-4570fb71e503
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=862738, tx_dropped=0, tx_errors=0, tx_packets=9222}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 29dd5cb732fe935246475811cdc9f2a3ac785435
Author:     Daniele Di Proietto &lt;daniele.di.proietto@gmail.com&gt;
AuthorDate: Thu Jan 23 23:26:42 2014 +0100
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Mon Feb 3 14:05:30 2014 -0800

    datapath: Added (unsigned long long) cast in printf
    
    This is necessary, since u64 is not unsigned long long
    in all architectures: u64 could be also uint64_t.
    
    Signed-off-by: Daniele Di Proietto &lt;daniele.di.proietto@gmail.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
