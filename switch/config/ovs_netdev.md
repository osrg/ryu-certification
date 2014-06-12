---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c74b1c9e-4e91-4180-b83f-5d5c7c6eb622
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 24e94fa3-4238-4824-bc2a-86e4aa5cc38f
controller          : [edc5d256-891a-4041-8fb9-14861945cc14]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2b7a5dda-c0a7-49b9-8c7a-899e108f36de, 70540843-722a-44d3-aff3-31f1a862d153, 7fa331a6-840a-4515-a592-139417d46edd, f36e4afb-eeca-4256-a246-eb94ef00a69b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : edc5d256-891a-4041-8fb9-14861945cc14
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=962, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2b7a5dda-c0a7-49b9-8c7a-899e108f36de
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [21fd1e54-ea8a-48e8-a5e4-a5464b29135d]
name                : br0

_uuid               : 7fa331a6-840a-4515-a592-139417d46edd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8fde4558-5612-4ba2-9b7f-6366c49d7f46]
name                : eth22

_uuid               : 70540843-722a-44d3-aff3-31f1a862d153
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [07555a94-44a1-427a-ac9f-047e339f2ba4]
name                : eth23

_uuid               : f36e4afb-eeca-4256-a246-eb94ef00a69b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [01435153-d31a-4125-be0b-8559a73db44f]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 21fd1e54-ea8a-48e8-a5e4-a5464b29135d
admin_state         : down
duplex              : full
ifindex             : 452
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

_uuid               : 8fde4558-5612-4ba2-9b7f-6366c49d7f46
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1559305296, tx_dropped=0, tx_errors=0, tx_packets=12517945}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 07555a94-44a1-427a-ac9f-047e339f2ba4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2137519408, tx_dropped=0, tx_errors=0, tx_packets=7151636}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 01435153-d31a-4125-be0b-8559a73db44f
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
statistics          : {collisions=0, rx_bytes=1246717364, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26669918, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 290ad78a64faaca2895cc0c22532169a73b7009d
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Wed Jun 11 09:28:05 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jun 11 17:11:49 2014 -0700

    ofproto-dpif: Add idle_timeout parameter to ofproto_dpif_add_internal_flow&#40;&#41;
    
    This is in preparation for using the same helper as part of support
    for using recirculation in conjunction series of actions including
    with MPLS actions that are currently not able to be translated.
    
    In that scenario the idle timeout will be used to expire internal
    rules that are added to handle recirculation.
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
