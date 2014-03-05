---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0971fd44-aab5-464b-a6fe-b1c3c720bc84
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7b8e8237-1ebb-421f-8eab-6f64a6bff4c5
controller          : [624f8dc8-2444-4de9-8855-900f73d95d97]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [22b8640a-2ab3-46d6-a790-70631e5b2525, 3e4c094e-875a-40e0-b091-1a771716a477, fd7482e8-f053-4933-9edf-500ec24368c9]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 624f8dc8-2444-4de9-8855-900f73d95d97
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=377, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : fd7482e8-f053-4933-9edf-500ec24368c9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a5abdd3f-a981-4ca7-b8a2-6a2a6c27df8c]
name                : eth7

_uuid               : 3e4c094e-875a-40e0-b091-1a771716a477
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9810af54-4e6e-4f6b-8470-cc845784ae21]
name                : br0

_uuid               : 22b8640a-2ab3-46d6-a790-70631e5b2525
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9738976e-0495-45c7-803a-2dfa1a257e60]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9810af54-4e6e-4f6b-8470-cc845784ae21
admin_state         : up
duplex              : full
ifindex             : 436
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

_uuid               : 9738976e-0495-45c7-803a-2dfa1a257e60
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3174676, tx_dropped=0, tx_errors=0, tx_packets=33879}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : a5abdd3f-a981-4ca7-b8a2-6a2a6c27df8c
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
statistics          : {collisions=0, rx_bytes=3061441654, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72616772, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit bae94bc77362b59a52c0f562e62ff96198dab9d0
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Mon Mar 3 14:13:03 2014 -0800
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Wed Mar 5 08:38:18 2014 -0800

    timeval: gettimeofday() for Windows.
    
    Use GetSystemTimePreciseAsFileTime() for gettimeofday().
    GetSystemTimePreciseAsFileTime() provides the result that is more
    high resolution than just the microsecond that gittimeofday() in
    Linux provides. So we need to remove some additional precision.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
