---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
753ea090-0a9e-48a0-abfa-aa78ef915dda
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7aac46eb-f084-4158-b30c-040f8809c584
controller          : [d4824a7e-1869-4efd-955c-2c00b5a3e450]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [51b744fa-088f-412d-9638-a6ab8e453443, 5c0233c3-a739-48c8-a715-39948ae965d9, 80f86dc3-0163-452d-b735-4d5a7ba37f6d, fbd27562-9bdf-43ae-83ce-5dbf580e4f66]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d4824a7e-1869-4efd-955c-2c00b5a3e450
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=672, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 51b744fa-088f-412d-9638-a6ab8e453443
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [50640087-dd08-4109-b9c6-a500aebb1ce1]
name                : eth22

_uuid               : fbd27562-9bdf-43ae-83ce-5dbf580e4f66
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [73f434f5-c744-4e1f-9cc6-476fab05b09f]
name                : eth21

_uuid               : 80f86dc3-0163-452d-b735-4d5a7ba37f6d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f7c7e621-06c3-460f-963a-ad64810f35d5]
name                : br0

_uuid               : 5c0233c3-a739-48c8-a715-39948ae965d9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f7726c70-f7b9-4d7a-afdd-e50f4966eec8]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f7726c70-f7b9-4d7a-afdd-e50f4966eec8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=622489408, tx_dropped=0, tx_errors=0, tx_packets=6141616}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 73f434f5-c744-4e1f-9cc6-476fab05b09f
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
statistics          : {collisions=0, rx_bytes=3389960703, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=108273287, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f7c7e621-06c3-460f-963a-ad64810f35d5
admin_state         : down
duplex              : full
ifindex             : 215
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

_uuid               : 50640087-dd08-4109-b9c6-a500aebb1ce1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3243869144, tx_dropped=0, tx_errors=0, tx_packets=62323951}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1f2e8d2d85ab7dac37653c4f9d034ce452f289ca
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Oct 7 12:59:14 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Oct 7 12:59:14 2014 -0700

    flow: Clean up MINIFLOW_FOR_EACH_IN_MAP.
    
    It seemed awkward to have declarations outside the for loop.
    
    This may also be a little faster because it avoids some calls to
    count_1bits&#40;&#41;.  The idea for that change is due to Jarno Rajahalme
    &lt;jrajahalme@nicira.com&gt;.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
