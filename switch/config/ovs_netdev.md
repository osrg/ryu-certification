---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4177d719-781c-4753-8e69-20aebd15fe96
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a1292305-56a6-43e1-a092-34919a3f198e
controller          : [0846765a-1840-4fc9-9410-63c0b61c4243]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0c8b9ee2-090a-4194-b230-1b044c7f3c43, 7f44afa8-396f-43e8-ae30-8535948292e3, e752da96-6765-45c4-b68b-37b7120d2371, f88f7bce-2fa2-40ab-96c3-e250bee7a378]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0846765a-1840-4fc9-9410-63c0b61c4243
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=982, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7f44afa8-396f-43e8-ae30-8535948292e3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [87f91fc0-9b7f-4a1f-8bdf-1cdb6adf7d0b]
name                : eth21

_uuid               : e752da96-6765-45c4-b68b-37b7120d2371
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [18c3eb67-d622-4ac8-8e9b-e5cb218f92ef]
name                : eth23

_uuid               : f88f7bce-2fa2-40ab-96c3-e250bee7a378
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8772fbe1-80ce-4233-b096-ddea15cf7753]
name                : eth22

_uuid               : 0c8b9ee2-090a-4194-b230-1b044c7f3c43
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3acc5305-51a0-47b9-a9b5-4f7e7dff4733]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 87f91fc0-9b7f-4a1f-8bdf-1cdb6adf7d0b
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
statistics          : {collisions=0, rx_bytes=426841317, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=89164527, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8772fbe1-80ce-4233-b096-ddea15cf7753
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1154932958, tx_dropped=0, tx_errors=0, tx_packets=35174998}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3acc5305-51a0-47b9-a9b5-4f7e7dff4733
admin_state         : down
duplex              : full
ifindex             : 627
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

_uuid               : 18c3eb67-d622-4ac8-8e9b-e5cb218f92ef
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=3266034580, tx_dropped=0, tx_errors=0, tx_packets=10767975}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c354fcc575718928224612f135b231f7e1584c2a
Author:     Thomas Graf &lt;tgraf@noironetworks.com&gt;
AuthorDate: Fri Jun 20 13:17:36 2014 +0200
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Jun 24 08:51:17 2014 -0700

    ovs-ofctl.8: Move mod-table out of group tables section
    
    Signed-off-by: Thomas Graf &lt;tgraf@noironetworks.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
