---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0f19fe95-c720-4556-92ac-bfa5ed39b4f9
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 83babb34-a02f-493d-aa04-14f70e7ecc84
controller          : [88d70d0d-41a0-4a87-a81f-f6c27a7ad19d]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [44a94824-106f-49f9-b04e-8e94448ba131, b037b0e2-f915-4b96-942e-6e51292b0488, fc1cd309-2060-478e-8c4f-3cd984b2b38d, fc638ab5-760f-496e-ae7a-1efdcf518e3e]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 88d70d0d-41a0-4a87-a81f-f6c27a7ad19d
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 44a94824-106f-49f9-b04e-8e94448ba131
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ea3bd5d2-0ee6-4c64-8647-2fe1a867696c]
name                : "eth23"

_uuid               : fc1cd309-2060-478e-8c4f-3cd984b2b38d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4ec056d3-ac03-4245-8477-46cc19e56a8e]
name                : "eth22"

_uuid               : fc638ab5-760f-496e-ae7a-1efdcf518e3e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2fa254e3-0bbf-4bce-b223-a1f1254d6204]
name                : "eth21"

_uuid               : b037b0e2-f915-4b96-942e-6e51292b0488
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [33168f41-6959-4f22-ad8b-2b0b31ad6f42]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 33168f41-6959-4f22-ad8b-2b0b31ad6f42
admin_state         : down
duplex              : full
ifindex             : 271
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

_uuid               : ea3bd5d2-0ee6-4c64-8647-2fe1a867696c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1176922500, tx_dropped=0, tx_errors=0, tx_packets=784615}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 4ec056d3-ac03-4245-8477-46cc19e56a8e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18089315792, tx_dropped=0, tx_errors=0, tx_packets=12064077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 2fa254e3-0bbf-4bce-b223-a1f1254d6204
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
statistics          : {collisions=0, rx_bytes=24024581534, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16026376, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1a16d008e6df913f65e038a6b91e84016d7bd749
Author:     Aaron Conole &lt;aaron@bytheb.org&gt;
AuthorDate: Mon Jul 20 19:13:51 2015 -0400
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Jul 21 10:39:23 2015 -0700

    vtep/automake.mk: Changes to support make distcheck.
    
    Add autogenerated files to the CLEANFILES so that they are not kept around
    after clean/distclean.
    
    Signed-off-by: Aaron Conole &lt;aaron@bytheb.org&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
