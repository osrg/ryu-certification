---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2a009336-6e6a-4d8f-9af6-441e672da32e
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 526b4a6f-f398-4ba7-808f-6cacc50e1ca6
controller          : [8d0d1e69-bdcb-49e3-804e-9967a9274a6a]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2ec82198-57d1-49f3-87e9-a14d2c02c3c3, 55080ce1-fd49-4695-96ca-1beb6b7521d2, f79a145a-5565-43f4-a2dc-e93b51f42fcd, fd31b17d-a6eb-47e8-a4c7-b0fb8e50a1c7]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8d0d1e69-bdcb-49e3-804e-9967a9274a6a
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="657", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2ec82198-57d1-49f3-87e9-a14d2c02c3c3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3060e85e-5a01-4c74-8675-b413f1bc2a56]
name                : "eth21"

_uuid               : 55080ce1-fd49-4695-96ca-1beb6b7521d2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8fcf8821-16c7-4cc6-88e3-a980b2f2b426]
name                : "eth23"

_uuid               : fd31b17d-a6eb-47e8-a4c7-b0fb8e50a1c7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d5926656-61c2-411f-96cd-0290978ac479]
name                : "br0"

_uuid               : f79a145a-5565-43f4-a2dc-e93b51f42fcd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b7630139-98ea-4fdb-a567-7a2b74c9a830]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8fcf8821-16c7-4cc6-88e3-a980b2f2b426
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=43212165000, tx_dropped=0, tx_errors=0, tx_packets=28808110}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b7630139-98ea-4fdb-a567-7a2b74c9a830
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=631521117500, tx_dropped=0, tx_errors=0, tx_packets=421185831}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d5926656-61c2-411f-96cd-0290978ac479
admin_state         : down
duplex              : full
ifindex             : 947
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

_uuid               : 3060e85e-5a01-4c74-8675-b413f1bc2a56
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
statistics          : {collisions=0, rx_bytes=1234648221286, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=823487827, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
