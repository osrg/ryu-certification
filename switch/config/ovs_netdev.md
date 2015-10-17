---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
279c8d6c-0b3d-4c25-b74e-43c133c3e040
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 4bce1b41-ca68-447a-9ec7-b037c4b7f8e3
controller          : [f1bf8e8c-0c28-4250-9715-ec26552de59b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2bee2da1-fd19-43f5-b915-3bf3a25cbece, 78f05a86-d00d-454e-af27-4fa868d2d838, c1b07bab-fe1e-4aa0-ba80-1efed9de4789, de22c3a8-3ac8-4888-8807-d90247c0494b]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f1bf8e8c-0c28-4250-9715-ec26552de59b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="757", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : de22c3a8-3ac8-4888-8807-d90247c0494b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3128b77f-ef39-4dfe-9a49-2de1ba30e561]
name                : "eth23"

_uuid               : 2bee2da1-fd19-43f5-b915-3bf3a25cbece
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3391c016-dcbf-455c-9eeb-50135de135b7]
name                : "eth22"

_uuid               : 78f05a86-d00d-454e-af27-4fa868d2d838
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [00b62e0b-3eb9-4fc9-bb22-302d89caa3d5]
name                : "eth21"

_uuid               : c1b07bab-fe1e-4aa0-ba80-1efed9de4789
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d5188d51-4efd-4e62-b50d-a9b9cde44c55]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d5188d51-4efd-4e62-b50d-a9b9cde44c55
admin_state         : down
duplex              : full
ifindex             : 575
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

_uuid               : 3391c016-dcbf-455c-9eeb-50135de135b7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=27402167188, tx_dropped=0, tx_errors=0, tx_packets=18280190}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 3128b77f-ef39-4dfe-9a49-2de1ba30e561
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3444778500, tx_dropped=0, tx_errors=0, tx_packets=2296519}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 00b62e0b-3eb9-4fc9-bb22-302d89caa3d5
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
statistics          : {collisions=0, rx_bytes=38312015594, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=25568581, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9975d7beb36ab3aadfd07c9d566f8d3d1d340fc4
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Oct 16 23:43:58 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Oct 16 23:52:41 2015 -0700

    ovn: Implement basic logical L3 routing.
    
    This implements basic logical L3 routing.  It has a lot of caveats,
    including the following regarding testing:
    
       * Only single-router hops have been tested.  Chains or trees of
         logical routers may work but definitely need testing and may
         need a little extra code.
    
       * No testing of logical router ARP replies.
    
       * Not enough testing in general.
    
    ovn/TODO describes a lot of other caveats in terms of the work needed
    to fix them.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
