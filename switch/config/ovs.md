---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
96388529-e304-4602-993d-3f6ca759a597
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth8"
            Interface "eth8"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth7"
            Interface "eth7"

$ sudo ovs-vsctl list Bridge
_uuid               : ed945438-9f37-4fa5-a844-aa53db49dae7
controller          : [477e3195-6fbd-4862-83f3-248329175cba]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0d087f2a-0357-462f-822c-44e6b946a4c5, 5b2784f2-e33d-4322-9eda-1c8c944b03ca, bd706c6a-c167-4064-bffd-9fc704ee37b1]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 477e3195-6fbd-4862-83f3-248329175cba
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="376", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 5b2784f2-e33d-4322-9eda-1c8c944b03ca
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [157e36d4-2f13-4685-b433-5ab4f830a357]
name                : "br0"

_uuid               : bd706c6a-c167-4064-bffd-9fc704ee37b1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [38d90161-a406-483c-842d-4d9bb01b1128]
name                : "eth7"

_uuid               : 0d087f2a-0357-462f-822c-44e6b946a4c5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d9a5d018-5cb8-45b0-849b-14660abc17ce]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : d9a5d018-5cb8-45b0-849b-14660abc17ce
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

_uuid               : 157e36d4-2f13-4685-b433-5ab4f830a357
admin_state         : up
ifindex             : 103
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

_uuid               : 38d90161-a406-483c-842d-4d9bb01b1128
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
