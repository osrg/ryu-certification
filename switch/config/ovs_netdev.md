---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
5ac40b38-6191-432e-a19c-e250f54cb4dd
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 2007dab1-ae90-43c5-96c3-bbca0411c05a
controller          : [d6b3b513-a06e-4e00-89e4-ffa03fa4a5b5]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [38da0736-f72f-43bb-bf51-77db685bc884, 625d0591-a90b-459d-8714-e35ee1df67ae, cf6b597c-2ca9-4bb5-90df-b4c38bbaa7ea, d31e755a-f435-41e0-9654-113551eea10e]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d6b3b513-a06e-4e00-89e4-ffa03fa4a5b5
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=672, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : cf6b597c-2ca9-4bb5-90df-b4c38bbaa7ea
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [728ef08e-d531-4b8d-9ecc-dcc7c9abe413]
name                : eth23

_uuid               : 625d0591-a90b-459d-8714-e35ee1df67ae
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9da53786-fb8f-4080-a62d-438351dde4dd]
name                : eth21

_uuid               : d31e755a-f435-41e0-9654-113551eea10e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [30f55dd0-1005-4eb6-b077-699fae2a1927]
name                : br0

_uuid               : 38da0736-f72f-43bb-bf51-77db685bc884
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4ef07330-9116-4e49-9222-0e593221a57f]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 30f55dd0-1005-4eb6-b077-699fae2a1927
admin_state         : down
duplex              : full
ifindex             : 65
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

_uuid               : 4ef07330-9116-4e49-9222-0e593221a57f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2196527196, tx_dropped=0, tx_errors=0, tx_packets=12924145}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9da53786-fb8f-4080-a62d-438351dde4dd
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
statistics          : {collisions=0, rx_bytes=272673320, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=17376096, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 728ef08e-d531-4b8d-9ecc-dcc7c9abe413
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2039310000, tx_dropped=0, tx_errors=0, tx_packets=1359540}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ffd9722066c76f65d543906884f0d4a6d9272cb4
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Wed Aug 27 08:21:45 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Wed Aug 27 08:21:45 2014 -0700

    lib/flow.h Revert bitfield back to uint64_t.
    
    Using different types for the two bitfields did not work on MSVC, so
    reverting back to &quot;64-bit bool&quot; :-&#41;
    
    Reported-by: Saurabh Shah &lt;ssaurabh@vmware.com&gt;
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
