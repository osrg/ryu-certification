---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
56b5f7a2-da35-4d55-a5d7-8ae16be61313
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : dec0cb0a-eb99-438b-86bc-5c0114660ae8
controller          : [2cbd714a-6d44-46ce-8ff5-f04036a6ccbe]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [41a29500-1652-4441-b74c-18e8da1fdcc5, 4ae7bfa8-9ea7-46fd-850f-9e21f7128c59, 809852fa-72e7-4b11-baf8-0498ca707e91, b6602eef-e39c-485a-8317-750c4819fa03]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2cbd714a-6d44-46ce-8ff5-f04036a6ccbe
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="647", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4ae7bfa8-9ea7-46fd-850f-9e21f7128c59
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [52d01768-3a48-4b78-80e1-6b690d2b6de6]
name                : "eth21"

_uuid               : 41a29500-1652-4441-b74c-18e8da1fdcc5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a96d9ad7-d2db-4245-90fa-4ae189ff1de3]
name                : "eth23"

_uuid               : 809852fa-72e7-4b11-baf8-0498ca707e91
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [31f8b28c-0259-40b0-9f35-c05ec795f318]
name                : "br0"

_uuid               : b6602eef-e39c-485a-8317-750c4819fa03
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ecb63f49-b9f7-46ae-bd4f-b9a38bd09bc3]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 52d01768-3a48-4b78-80e1-6b690d2b6de6
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
statistics          : {collisions=0, rx_bytes=1234765096111, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=823566386, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 31f8b28c-0259-40b0-9f35-c05ec795f318
admin_state         : down
duplex              : full
ifindex             : 949
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

_uuid               : ecb63f49-b9f7-46ae-bd4f-b9a38bd09bc3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=631573518277, tx_dropped=0, tx_errors=0, tx_packets=421221069}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a96d9ad7-d2db-4245-90fa-4ae189ff1de3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=43299996000, tx_dropped=0, tx_errors=0, tx_packets=28866664}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d7d417fcddf972ee14e678352017daaf626437fa
Author:     Terry Wilson &lt;twilson@redhat.com&gt;
AuthorDate: Sat Apr 25 14:57:44 2015 -0500
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Apr 27 08:31:39 2015 -0700

    Allow subclasses of Idl to define a notification hook
    
    It is useful to make the notification events that Idl processes
    accessible to users of the library. This will make it possible to
    keep external systems in sync, but does not impose any particular
    notification pattern.
    
    The Row.from_json&#40;&#41; call is added to be able to convert the 'old'
    JSON response on an update to a Row object to make it easy for
    users of notify&#40;&#41; to see what changed, though this usage of Row
    is quite different than Idl's typical use.
    
    Signed-off-by: Terry Wilson &lt;twilson@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
