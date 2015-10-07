---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
209e92b2-2843-428a-bc28-988a98f1252f
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f104f3b8-bedc-4159-adeb-24cc8e213961
controller          : [9e4d92f4-9d06-44fd-b269-26323907866b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [060a2241-673f-41be-9e5d-a40c684cea87, 1f92edd0-5e5d-42ad-bb6d-98e120afcbaa, 4d3dc7c9-57f2-4280-bc2e-a90caddb1faf, 8ab7b4a5-245d-4403-ad24-764a63ddbcfd]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9e4d92f4-9d06-44fd-b269-26323907866b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="752", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1f92edd0-5e5d-42ad-bb6d-98e120afcbaa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f16a1caa-5ed3-4353-a1b3-e0fcf94f1ce6]
name                : "eth22"

_uuid               : 8ab7b4a5-245d-4403-ad24-764a63ddbcfd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4a7c71df-3ded-40d0-81c8-292d667336cb]
name                : "br0"

_uuid               : 060a2241-673f-41be-9e5d-a40c684cea87
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8e8f2ad0-9be3-47f2-82c8-fbeaa9e26191]
name                : "eth21"

_uuid               : 4d3dc7c9-57f2-4280-bc2e-a90caddb1faf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [166e7f07-e41e-4f61-a7de-710d425a8a4e]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8e8f2ad0-9be3-47f2-82c8-fbeaa9e26191
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=36322711429, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=24231445, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f16a1caa-5ed3-4353-a1b3-e0fcf94f1ce6
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=26507784370, tx_dropped=0, tx_errors=0, tx_packets=17679254}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 166e7f07-e41e-4f61-a7de-710d425a8a4e
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1952770500, tx_dropped=0, tx_errors=0, tx_packets=1301847}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 4a7c71df-3ded-40d0-81c8-292d667336cb
admin_state         : down
duplex              : full
ifindex             : 541
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c96ba5023de2fc0eca89b133f673b7b8e43d8276
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Oct 6 15:52:54 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Oct 6 15:52:54 2015 -0700

    ovn-sb.xml: Reorganize Port_Binding documentation.
    
    This takes advantage of column grouping and the ability to document a key
    within a column.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
