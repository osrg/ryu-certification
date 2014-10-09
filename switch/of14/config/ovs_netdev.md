---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
24b52699-00bb-40b0-80ca-4e4804b40590
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : cf5cb305-41d3-4c81-bc31-b5e95e9191ab
controller          : [ef7dfc64-7cc9-46a1-bca0-119c4ab15fb8]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [3688e949-547d-4fca-9514-9b4265e86d9c, 4bae5089-ed72-4167-a811-f867f784280b, 868ab5d7-399d-4f71-9bb7-46b416446b59, 8cccc766-8653-47db-bd7e-00d2605bcdc0]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ef7dfc64-7cc9-46a1-bca0-119c4ab15fb8
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=742, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4bae5089-ed72-4167-a811-f867f784280b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6e62bcd5-8741-4db1-b5eb-314d8338a217]
name                : eth21

_uuid               : 3688e949-547d-4fca-9514-9b4265e86d9c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [610798d8-8e6e-4c42-abfe-f034b5c3fa54]
name                : br0

_uuid               : 8cccc766-8653-47db-bd7e-00d2605bcdc0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f372fafc-e7c9-4f44-8682-17d32e2b2480]
name                : eth23

_uuid               : 868ab5d7-399d-4f71-9bb7-46b416446b59
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e5d4e1f0-45d2-435b-a37e-0fbf92d46cbd]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e5d4e1f0-45d2-435b-a37e-0fbf92d46cbd
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1772933604, tx_dropped=0, tx_errors=0, tx_packets=72798442}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 610798d8-8e6e-4c42-abfe-f034b5c3fa54
admin_state         : down
duplex              : full
ifindex             : 225
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

_uuid               : f372fafc-e7c9-4f44-8682-17d32e2b2480
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1128799408, tx_dropped=0, tx_errors=0, tx_packets=6479156}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6e62bcd5-8741-4db1-b5eb-314d8338a217
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
statistics          : {collisions=0, rx_bytes=642582155, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=123625739, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 24adf5d6842b30006d35759b475fd15666670b5e
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Wed Oct 8 17:15:42 2014 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Thu Oct 9 11:40:02 2014 -0700

    ovs-bugtool: Add fdb output for all bridges
    
    Fdb entries can provide useful information. Collect them in bugtool.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
