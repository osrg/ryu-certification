---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0cb8e39e-4248-4f73-a138-89da82e5edb8
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ac14493d-8430-4a35-bea7-19f501bafa2f
controller          : [78e926d0-8aa1-4b9c-8bd5-127b445c4a5d]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2015161d-a3d8-4f5f-9f4a-1e515c15dfee, 8536de6b-6c59-4dc4-9dae-bb49d3e192a8, 9e67f898-4b4b-449b-8c10-bc5ef02aabe2, f508b928-1e59-49ff-a703-f540c3b18271]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 78e926d0-8aa1-4b9c-8bd5-127b445c4a5d
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=566, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9e67f898-4b4b-449b-8c10-bc5ef02aabe2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [576eb07f-2ff2-4943-8a2b-bec347323cf0]
name                : eth23

_uuid               : f508b928-1e59-49ff-a703-f540c3b18271
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8f2e95b0-256e-44cd-a4c5-02127a350cb6]
name                : eth21

_uuid               : 2015161d-a3d8-4f5f-9f4a-1e515c15dfee
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e401b347-86be-4fee-a654-d0f421442387]
name                : br0

_uuid               : 8536de6b-6c59-4dc4-9dae-bb49d3e192a8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [061cca03-b1a6-4b84-ab6a-f8e28fba3f5f]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8f2e95b0-256e-44cd-a4c5-02127a350cb6
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=935117830, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=626545, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 576eb07f-2ff2-4943-8a2b-bec347323cf0
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=730977000, tx_dropped=0, tx_errors=0, tx_packets=487318}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e401b347-86be-4fee-a654-d0f421442387
admin_state         : down
duplex              : full
ifindex             : 57
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 061cca03-b1a6-4b84-ab6a-f8e28fba3f5f
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=320933210, tx_dropped=0, tx_errors=0, tx_packets=215091}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit b10d46a600136f3df25a7f4b7bfc275de0fb6367
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Thu May 8 12:37:52 2014 +1200
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Mon May 19 16:25:49 2014 +1200

    tests: Check dpif-netdev odp_actions consistency.
    
    Ensure that upcall key matches flow install and flow_dump for userspace
    datapath. This was previously assumed, but not tested. This makes the
    assumption more explicit.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
