---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f025972c-2413-4fee-8f02-bff13420bce3
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
_uuid               : a5278475-35b4-4a87-b120-6ee820d90086
controller          : [f29c50b7-fa54-4e65-8991-954cbe31b5a3]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [30ba9b07-944c-42bb-9390-a89be4bfc1db, 5936636a-3f37-4506-9ebe-7d6ea0cbd6f2, 7889745e-5c42-42fa-99da-5acfe91012a2]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : f29c50b7-fa54-4e65-8991-954cbe31b5a3
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="297", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 5936636a-3f37-4506-9ebe-7d6ea0cbd6f2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b69c7416-a24d-4934-84b9-90d5225a6f9c]
name                : "eth7"

_uuid               : 7889745e-5c42-42fa-99da-5acfe91012a2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7b85c9d3-add4-40b2-85e7-d7b6056748f7]
name                : "eth8"

_uuid               : 30ba9b07-944c-42bb-9390-a89be4bfc1db
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [eefb5fab-dfd5-449c-8ed0-e1de297508fe]
name                : "br0"

$ sudo ovs-vsctl list Interface
_uuid               : b69c7416-a24d-4934-84b9-90d5225a6f9c
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
statistics          : {collisions=0, rx_bytes=2072801, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=21082, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : eefb5fab-dfd5-449c-8ed0-e1de297508fe
admin_state         : up
duplex              : full
ifindex             : 101
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

_uuid               : 7b85c9d3-add4-40b2-85e7-d7b6056748f7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=707476, tx_dropped=0, tx_errors=0, tx_packets=7634}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d02c42bf4d8ecb0723ca5c6a3156c480949344a4
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Tue Jan 7 00:17:25 2014 -0800
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Tue Jan 7 20:18:10 2014 -0800

    ofproto-dpif: Fix a vlan-splinter megaflow bug
    
    When vlan-splinter is enabled, ovs receives non-vlan flows from the
    kernel vlan ports, vlan tag is then added to the incoming flow before
    xlating, so that they look like those received from a trunk port.
    
    In case megaflow is enabled, xlating may set vlan masks during rule
    processing as usual. If those vlan masks were serialized and downloaded
    to the kernel (this bug), those mega flows will be rejected due to
    unexpected vlan mask encapsulation, since the original kernel flows do
    not have vlan tags. This bug does not break connectivity, but impacts
    performance since all traffic received on vlan splinter ports will now
    be handled by vswitchd, as no datapath flows can be successfully
    installed.
    
    This fix is to make sure no vlan mask encapsulation is generated for
    the datapath flow if its in_port was re-written by vlan-splinter
    receiving logic.
    
    Bug #22567
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
