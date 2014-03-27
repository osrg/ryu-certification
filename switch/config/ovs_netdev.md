---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
487936b9-7e75-43f2-b524-f3097096002a
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e367c01b-6600-4057-9b2e-2dc6b62a7cf1
controller          : [2ead2e7b-ad23-4a54-9a6e-880cf9efb7e7]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [6b087fb8-0514-4103-9341-1a5c72998439, 85ab6a75-c92c-4d3d-9091-189e389e0af4, de74e48d-5bef-44c9-8a74-9462c7a3d395]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2ead2e7b-ad23-4a54-9a6e-880cf9efb7e7
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=312, sec_since_disconnect=7, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6b087fb8-0514-4103-9341-1a5c72998439
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f8032b1e-8fc5-4f1e-b1cd-1b3f82026054]
name                : eth8

_uuid               : 85ab6a75-c92c-4d3d-9091-189e389e0af4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bb0f6105-55f3-4938-89af-3d1d64b42bcb]
name                : eth7

_uuid               : de74e48d-5bef-44c9-8a74-9462c7a3d395
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2d9f4d10-4282-41a9-9b36-00fa917c11b6]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2d9f4d10-4282-41a9-9b36-00fa917c11b6
admin_state         : up
duplex              : full
ifindex             : 744
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : bb0f6105-55f3-4938-89af-3d1d64b42bcb
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=3069831832, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72701865, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : f8032b1e-8fc5-4f1e-b1cd-1b3f82026054
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5657528, tx_dropped=0, tx_errors=0, tx_packets=60310}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5a51b2cd3483c6c1719e5ef7091f558d49431351
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Tue Mar 25 15:26:23 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Tue Mar 25 15:26:23 2014 -0700

    lib/ofpbuf: Remove 'l7' pointer.
    
    Now that we don't need to parse TCP flags from the packet after
    extraction, we usually do not need the 'l7' pointer any more.  When
    needed, ofpbuf_get_tcp|udp|sctp|icmp_payload() or ofpbuf_get_l4_size()
    can be used instead.
    
    Removal of 'l7' was requested by Pravin for the DPDK datapath work, as
    it simplifies packet parsing a bit.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
