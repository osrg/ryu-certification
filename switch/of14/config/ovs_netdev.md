---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a5488604-2642-4114-b6be-578601e8d0d5
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 9fe570a2-1de3-4151-9d05-6944b605ff90
controller          : [8f5543bf-9d44-42de-a94f-379923d1e099]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0596d527-4fc0-4b89-a843-1a0f849a4a8b, 4682a837-ff92-4c40-836d-675ea636a1d6, 7829d112-6528-4a35-99b3-769b03bbd209, ba7f623f-a6ae-45f3-be78-0fc20ac956ea]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8f5543bf-9d44-42de-a94f-379923d1e099
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7829d112-6528-4a35-99b3-769b03bbd209
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e10a4889-0802-4bb7-a9fd-8bd7bf95358a]
name                : "eth21"

_uuid               : 0596d527-4fc0-4b89-a843-1a0f849a4a8b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fd65aeb2-8d27-42b7-af1b-6903a4dd3c32]
name                : "eth23"

_uuid               : ba7f623f-a6ae-45f3-be78-0fc20ac956ea
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [10c36d34-3e2f-4590-bbb9-31bfa93054dc]
name                : "eth22"

_uuid               : 4682a837-ff92-4c40-836d-675ea636a1d6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d21d3f77-5d03-4682-baeb-955fd96334f1]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 10c36d34-3e2f-4590-bbb9-31bfa93054dc
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

_uuid               : e10a4889-0802-4bb7-a9fd-8bd7bf95358a
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

_uuid               : fd65aeb2-8d27-42b7-af1b-6903a4dd3c32
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

_uuid               : d21d3f77-5d03-4682-baeb-955fd96334f1
admin_state         : down
duplex              : full
ifindex             : 453
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
commit 9d4aeccaf69861616cb0715d10e3f1f3e2a14e51
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed Aug 26 22:40:11 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Sep 11 20:01:10 2015 -0700

    expr: Properly handle several cases involving string variables.
    
    The expr test cases covered string variables poorly and thus a number of
    bugs and omissions slipped through.  This fixes them and generalizes the
    test cases to better cover string variables.
    
    Reported-by: Justin Pettit &lt;jpettit@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
