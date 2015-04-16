---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ea9f3122-42af-4b5a-847b-28238d405f86
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 97dc403b-9471-4cec-8209-22fa4b9376f4
controller          : [1757803b-59cc-471e-819e-a19cba20131c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1de56d7e-663f-49ff-b242-3f840dcb4cd0, 34567e76-f025-4683-9c25-90b70e54cffd, 40490f2f-d310-4700-b291-510555499343, 74e36f12-314e-4a58-8007-3e8e87e58697]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 1757803b-59cc-471e-819e-a19cba20131c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="647", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 34567e76-f025-4683-9c25-90b70e54cffd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b97596bd-c7c9-45d2-8c70-7e242808be88]
name                : "eth22"

_uuid               : 1de56d7e-663f-49ff-b242-3f840dcb4cd0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b6e3d778-54f7-418f-b0b0-4b034933df00]
name                : "br0"

_uuid               : 74e36f12-314e-4a58-8007-3e8e87e58697
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aab5ace0-2f45-4059-92f8-76d8ef684bf0]
name                : "eth23"

_uuid               : 40490f2f-d310-4700-b291-510555499343
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c61b498d-dbc6-40b7-a1d1-55901ea45b6f]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : aab5ace0-2f45-4059-92f8-76d8ef684bf0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=41721805500, tx_dropped=0, tx_errors=0, tx_packets=27814537}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b6e3d778-54f7-418f-b0b0-4b034933df00
admin_state         : down
duplex              : full
ifindex             : 913
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

_uuid               : b97596bd-c7c9-45d2-8c70-7e242808be88
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=630626756791, tx_dropped=0, tx_errors=0, tx_packets=420584420}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c61b498d-dbc6-40b7-a1d1-55901ea45b6f
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
statistics          : {collisions=0, rx_bytes=1232660723761, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=822151907, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c3db81e3eda7168287c421e4e6b3b53086e2238c
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Thu Apr 16 11:23:47 2015 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Thu Apr 16 13:27:08 2015 -0700

    datapath:netdevice: Export rpl_skb_gso_segment.
    
    With the latest change of separating vports into their own modules,
    we also need to explicitly export rpl_skb_gso_segment to avoid linker
    error.
    
    VMware-BZ: #1432578
    VMware-BZ: #1308175
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
