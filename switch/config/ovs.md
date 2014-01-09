---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
440bcb4c-c159-4140-a48c-e6927a816834
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth7"
            Interface "eth7"
        Port "eth8"
            Interface "eth8"

$ sudo ovs-vsctl list Bridge
_uuid               : ea6a9552-d78b-4bee-bfda-0b106deb7a91
controller          : [026a086a-d8ae-4bd7-97e0-e8caf7b08c50]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [07703ec7-adbf-408b-87ff-30db9f22e26e, 3e3b9aea-06d5-411c-893c-fcc76d671e40, c5fc9a8c-717b-4333-a816-4fd61a8de023]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 026a086a-d8ae-4bd7-97e0-e8caf7b08c50
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="352", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : c5fc9a8c-717b-4333-a816-4fd61a8de023
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [30036277-9501-4459-852c-dc445cc8cd72]
name                : "eth8"

_uuid               : 3e3b9aea-06d5-411c-893c-fcc76d671e40
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [16a77ae6-2d2e-43f3-88cd-6b9c824326a9]
name                : "eth7"

_uuid               : 07703ec7-adbf-408b-87ff-30db9f22e26e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [683a8505-7634-4a00-8235-d0b00e5c63c6]
name                : "br0"

$ sudo ovs-vsctl list Interface
_uuid               : 683a8505-7634-4a00-8235-d0b00e5c63c6
admin_state         : up
ifindex             : 123
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 16a77ae6-2d2e-43f3-88cd-6b9c824326a9
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "eth7"
ofport              : 1
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 30036277-9501-4459-852c-dc445cc8cd72
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:ec"
mtu                 : 1550
name                : "eth8"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6c3eee823e95d13c613935f0252c8a523bc6ef20
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Dec 27 17:00:30 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jan 8 17:13:32 2014 -0800

    dpif-netdev: Use separate threads for forwarding.
    
    For now, we use exactly two threads.  Presumably at some point we will want
    to make this configurable.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
