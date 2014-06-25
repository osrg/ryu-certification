---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2000d727-efbb-4637-ba60-425cf8be2d22
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b16a08eb-ecc2-4825-87f9-57fd23e6b67d
controller          : [6a4a1ec2-8970-41da-9225-6d26ff4fc02b]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [01a0a956-b2ad-4ec0-90d9-dbdf08b2e624, 87b6ac9b-964f-4669-b8c9-956641f0e82c, b2265edc-0be4-4a86-a8c7-411b93adefdc, cb2444ee-e6b1-4147-8668-1a9f9fe158d8]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6a4a1ec2-8970-41da-9225-6d26ff4fc02b
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=981, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b2265edc-0be4-4a86-a8c7-411b93adefdc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4813d877-3028-42ff-836e-b1d481a02324]
name                : eth22

_uuid               : 01a0a956-b2ad-4ec0-90d9-dbdf08b2e624
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [60030c9a-f298-40d8-878f-a345d40800e8]
name                : eth23

_uuid               : cb2444ee-e6b1-4147-8668-1a9f9fe158d8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e0b9f9c8-bb5e-4016-ad6b-420feed7c461]
name                : br0

_uuid               : 87b6ac9b-964f-4669-b8c9-956641f0e82c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f257ac23-5f58-4527-b672-1e176d52c805]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e0b9f9c8-bb5e-4016-ad6b-420feed7c461
admin_state         : down
ifindex             : 704
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 60030c9a-f298-40d8-878f-a345d40800e8
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2113756284, tx_dropped=0, tx_errors=0, tx_packets=12863101}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f257ac23-5f58-4527-b672-1e176d52c805
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
statistics          : {collisions=0, rx_bytes=4156143036, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=91670705, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 4813d877-3028-42ff-836e-b1d481a02324
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2465610380, tx_dropped=0, tx_errors=0, tx_packets=36056181}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7b7c2a463d4a56c33bfb8466b8dc3b6de9494991
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed Jun 25 11:39:25 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jun 25 11:39:25 2014 -0700

    json: Fix parsing of strings that end with a backslash.
    
    json_string_unescape&#40;&#41; flagged a backslash at the end of a string as an
    error, but of course &quot;\&quot; is a valid string.  This fixes the problem.
    
    VMware-BZ: #1275208
    Reported-by: Michael Hu &lt;mhu@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
