---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e7105343-3343-43c2-9056-92ce06447661
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : bbeeac0c-4ce4-4f34-8243-758e458226db
controller          : [d3117cdf-491b-4969-af90-65744040e4cf]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [879297c6-056d-4296-b6e7-aca4ea8fb6d4, b83098ec-65f3-449f-a800-da2a2d92c03a, c666d064-8fc9-4b24-836f-866b496fbd74]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d3117cdf-491b-4969-af90-65744040e4cf
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=351, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b83098ec-65f3-449f-a800-da2a2d92c03a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c6d0f33f-2239-4499-a8e5-ee145a45ac64]
name                : eth8

_uuid               : c666d064-8fc9-4b24-836f-866b496fbd74
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [63dbad5f-2101-4323-a51e-fa89b02f2f8b]
name                : br0

_uuid               : 879297c6-056d-4296-b6e7-aca4ea8fb6d4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [88d4dfde-608a-4d71-a8b1-7dde966cfec7]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 88d4dfde-608a-4d71-a8b1-7dde966cfec7
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

_uuid               : 63dbad5f-2101-4323-a51e-fa89b02f2f8b
admin_state         : up
ifindex             : 43
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

_uuid               : c6d0f33f-2239-4499-a8e5-ee145a45ac64
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit feb8a80bb9621f17ed0a249c79b0d02e9543e64a
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Jan 10 11:36:35 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Jan 10 11:36:35 2014 -0800

    ofproto: Add more thread safety annotations.
    
    These would have found the problem fixed in commit c7be3f559349 (connmgr:
    Fix attempt to take mutex recursively when exiting fail-open.).
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
