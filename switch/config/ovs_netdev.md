---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
88e081f4-87db-40a5-80fe-921751d8322e
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
_uuid               : 49876f5a-e203-48d8-83dd-19a7a538305d
controller          : [39bc66bf-5bca-4349-aa7f-58eb2aca7cbf]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [d2de16b4-09f4-48a7-8921-7adf92b61d78, f2df0b22-5cac-41d2-842f-5f2916f8062d, fb0380b5-4493-4d72-9de5-af620cc05d19]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 39bc66bf-5bca-4349-aa7f-58eb2aca7cbf
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=297, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d2de16b4-09f4-48a7-8921-7adf92b61d78
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4124096a-9c6c-4ae1-a61e-fc35ca4ce005]
name                : br0

_uuid               : fb0380b5-4493-4d72-9de5-af620cc05d19
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [53c641fc-c63d-4513-b20b-0fb814a38e74]
name                : eth7

_uuid               : f2df0b22-5cac-41d2-842f-5f2916f8062d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f6ee4872-31e2-4ba8-af52-690c9623f4a5]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 53c641fc-c63d-4513-b20b-0fb814a38e74
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
statistics          : {collisions=0, rx_bytes=3055839934, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72560092, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 4124096a-9c6c-4ae1-a61e-fc35ca4ce005
admin_state         : up
duplex              : full
ifindex             : 202
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

_uuid               : f6ee4872-31e2-4ba8-af52-690c9623f4a5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1445214, tx_dropped=0, tx_errors=0, tx_packets=15441}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 13af13b3e42977ef784dddafec1095a604f27e6c
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Fri Feb 7 12:50:17 2014 -0800
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Fri Feb 7 16:49:33 2014 -0800

    netdev-dummy: disable periodic probing
    
    netdev-dummy is mostly useed over reliable link for testing. Periodic
    probing over those links seem overkill.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
