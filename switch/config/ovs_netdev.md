---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3d7a2c70-890c-4905-ad57-74fc17c2d615
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : de903639-f98a-4031-a39e-d24368886ed1
controller          : [66114657-61a3-48ac-a69e-7f7c9424d903]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1a2dadc2-cc33-4387-bf4d-4c366e973a3d, 4e0c76a6-3c41-41ad-be84-e32d7396cf8c, 6a750578-6c38-49d5-a5a8-142725164446, a294d08e-e900-409a-95b5-0dcc376298c9]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 66114657-61a3-48ac-a69e-7f7c9424d903
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="657", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6a750578-6c38-49d5-a5a8-142725164446
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [17ec5df6-64eb-45be-82ca-19561d697dad]
name                : "eth23"

_uuid               : 1a2dadc2-cc33-4387-bf4d-4c366e973a3d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ace60a15-e7d2-4fad-bb17-a858f19c4249]
name                : "br0"

_uuid               : 4e0c76a6-3c41-41ad-be84-e32d7396cf8c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f43f75bb-5fdf-4f5d-8694-f4c491ac43a1]
name                : "eth22"

_uuid               : a294d08e-e900-409a-95b5-0dcc376298c9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1b192793-cb82-4329-a448-fbd34811df14]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ace60a15-e7d2-4fad-bb17-a858f19c4249
admin_state         : down
duplex              : full
ifindex             : 865
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

_uuid               : 17ec5df6-64eb-45be-82ca-19561d697dad
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=39658402500, tx_dropped=0, tx_errors=0, tx_packets=26438935}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f43f75bb-5fdf-4f5d-8694-f4c491ac43a1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=619848675604, tx_dropped=0, tx_errors=0, tx_packets=413391585}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1b192793-cb82-4329-a448-fbd34811df14
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
statistics          : {collisions=0, rx_bytes=1218613899140, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=812771178, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6c6045a72a93f72317567cc6075ac306ef0a3c44
Author:     Alin Serdean &lt;aserdean@cloudbasesolutions.com&gt;
AuthorDate: Mon Apr 6 17:22:06 2015 +0000
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Apr 6 11:06:22 2015 -0700

    datapath-windows Release lock on HVUpdateNIC
    
    Release switchContext-&gt;dispatchLock in case the vport has not been found.
    
    Acked-by: Eitan Eliahu &lt;eliahue@vmware.com&gt;
    Acked-by: Sorin Vinturis &lt;svinturis@cloudbasesolutions.com&gt;
    Signed-off-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
