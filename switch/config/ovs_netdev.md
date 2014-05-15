---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f8145d88-a79e-4cb3-9686-1e396036441e
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e0f78b40-530c-4f68-8c8c-a4c6cd4ce034
controller          : [7a9a08d7-c179-4b95-92d8-831efe7b3d4b]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [02d617e6-25fd-4fd2-988c-d0a3bca66805, 2d6a9a3a-5043-4bc3-b1b7-2f35c54ff6a4, 3990365b-b90b-403e-a725-de1a5bd17f92, c3edcc55-0474-4aef-a7a2-c095c0f3b626]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7a9a08d7-c179-4b95-92d8-831efe7b3d4b
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=557, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c3edcc55-0474-4aef-a7a2-c095c0f3b626
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [164a5a23-2e2f-476c-830a-0a44d6e01ac2]
name                : eth22

_uuid               : 02d617e6-25fd-4fd2-988c-d0a3bca66805
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0affca19-207a-45a7-ac89-399667fd6b3f]
name                : eth21

_uuid               : 2d6a9a3a-5043-4bc3-b1b7-2f35c54ff6a4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c17ce8d0-aa1c-4d3d-8cbc-3fdb73c1df38]
name                : eth23

_uuid               : 3990365b-b90b-403e-a725-de1a5bd17f92
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b09c33b0-b151-4f6b-8bcf-af05880fbaf1]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c17ce8d0-aa1c-4d3d-8cbc-3fdb73c1df38
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2694348000, tx_dropped=0, tx_errors=0, tx_packets=1796232}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b09c33b0-b151-4f6b-8bcf-af05880fbaf1
admin_state         : down
duplex              : full
ifindex             : 196
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

_uuid               : 0affca19-207a-45a7-ac89-399667fd6b3f
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
statistics          : {collisions=0, rx_bytes=3889396155, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2609397, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 164a5a23-2e2f-476c-830a-0a44d6e01ac2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1560806552, tx_dropped=0, tx_errors=0, tx_packets=1046603}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 2c7ea58953128e7a8692a9f28d388d0311dda84d
Author:     Justin Pettit &lt;jpettit@nicira.com&gt;
AuthorDate: Thu May 15 14:12:06 2014 -0700
Commit:     Justin Pettit &lt;jpettit@nicira.com&gt;
CommitDate: Thu May 15 14:12:06 2014 -0700

    Prepare for post-2.3.0 &#40;2.3.90&#41;.
    
    Signed-off-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
