---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2f3d6015-a5ff-48d7-b168-7f18621adcb2
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
_uuid               : ffbae5d3-49de-4922-8d13-716afcccf11a
controller          : [d9445d13-d4ae-4f6f-ad36-773028e8ef46]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [45547afc-b364-401d-a536-040ae2128919, 6cefb589-709b-4bc7-9d7e-dbbf36c7ed14, a765fe0d-88ca-471d-84ab-ce187121881f]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d9445d13-d4ae-4f6f-ad36-773028e8ef46
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=381, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 45547afc-b364-401d-a536-040ae2128919
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8f75ced5-4505-474d-bc68-ed31a07e78b1]
name                : br0

_uuid               : a765fe0d-88ca-471d-84ab-ce187121881f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9ad871ae-fe71-4243-a982-a0b73870cbd5]
name                : eth8

_uuid               : 6cefb589-709b-4bc7-9d7e-dbbf36c7ed14
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d854d537-5af0-400b-a62d-c82b410b112f]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8f75ced5-4505-474d-bc68-ed31a07e78b1
admin_state         : up
duplex              : full
ifindex             : 682
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

_uuid               : 9ad871ae-fe71-4243-a982-a0b73870cbd5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5083092, tx_dropped=0, tx_errors=0, tx_packets=54197}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : d854d537-5af0-400b-a62d-c82b410b112f
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
statistics          : {collisions=0, rx_bytes=3067924474, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72682538, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5deff5aa263a72a99141e95e50821f77bc687f15
Author:     Alexander Wu &lt;alexander.wu@huawei.com&gt;
AuthorDate: Sun Mar 23 23:20:04 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Sun Mar 23 23:27:00 2014 -0700

    ofp-util: Implement OFPMP_TABLE_FEATURES decoding and printing.
    
    Signed-off-by: Alexander Wu &lt;alexander.wu@huawei.com&gt;
    Co-authored-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
