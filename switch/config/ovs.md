---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
42a26c3c-2450-4587-b88b-227331d98991
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 9ecadfb0-99e9-4164-998a-8aedb5ded243
controller          : [25b31607-ac64-4b7b-9e23-41c416361d79]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [7db7e048-d4ac-4d90-9875-fff74f937939, ab24dfdc-c949-40ac-aa5e-3d01dc77e46a, fa7294a6-2564-4eee-b427-92eaf3507a3f]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 25b31607-ac64-4b7b-9e23-41c416361d79
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7db7e048-d4ac-4d90-9875-fff74f937939
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9e5708e3-b9a3-4b73-9397-8d97a699f053]
name                : br0

_uuid               : ab24dfdc-c949-40ac-aa5e-3d01dc77e46a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d4341f4f-cdcc-4158-918f-70e3062d5792]
name                : eth7

_uuid               : fa7294a6-2564-4eee-b427-92eaf3507a3f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4c473e3a-e353-47ec-9e18-0024b19b94d6]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4c473e3a-e353-47ec-9e18-0024b19b94d6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : d4341f4f-cdcc-4158-918f-70e3062d5792
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
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 9e5708e3-b9a3-4b73-9397-8d97a699f053
admin_state         : up
ifindex             : 113
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f87d3302c4e01189c437fafa4f0639c604962b18
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Mon Dec 9 17:28:32 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Jan 31 11:31:24 2014 -0800

    socket-util: Remove unused functions.
    
    A Windows porter mentioned to me that these functions caused special
    trouble in the Windows port.  However, they are no longer used, so we
    might as well remove them.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
