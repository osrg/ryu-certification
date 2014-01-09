---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0f997b04-b7be-41e4-830e-a3974faddd4b
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth8"
            Interface "eth8"
        Port "eth7"
            Interface "eth7"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge
_uuid               : f472b2c9-ae6b-46ee-85d6-a99f719b8d78
controller          : [e344dae5-d278-4f12-9c8f-0852b7b811cb]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [313e7cbf-30d8-471e-8c68-4a5400e5c035, 56c8add0-0758-49df-ad75-321c4aaa734d, a3005b8f-ee49-43e9-8b90-6544d168a0da]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : e344dae5-d278-4f12-9c8f-0852b7b811cb
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="297", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 56c8add0-0758-49df-ad75-321c4aaa734d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [139d0b5a-0d3b-4fd2-8216-cc7a56b7201e]
name                : "eth7"

_uuid               : a3005b8f-ee49-43e9-8b90-6544d168a0da
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f29f42da-bc89-491a-97f9-fd7e36f7c1e9]
name                : "br0"

_uuid               : 313e7cbf-30d8-471e-8c68-4a5400e5c035
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dbed1294-8584-46a3-beb2-5e8fb352b4b3]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : dbed1294-8584-46a3-beb2-5e8fb352b4b3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=952768, tx_dropped=0, tx_errors=0, tx_packets=10274}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 139d0b5a-0d3b-4fd2-8216-cc7a56b7201e
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
statistics          : {collisions=0, rx_bytes=2855981, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29002, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : f29f42da-bc89-491a-97f9-fd7e36f7c1e9
admin_state         : up
duplex              : full
ifindex             : 125
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
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
