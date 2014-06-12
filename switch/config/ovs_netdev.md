---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
711c512e-2507-4062-b4ef-d8b9e927f1ef
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
_uuid               : eee8726d-10d6-4cf3-b192-be80989dae94
controller          : [c976cd19-9b97-4ba5-8d9e-cfd2adec3bd1]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2fa21197-cbed-431f-9435-c5ece9e2e98c, 592737e6-37fc-44e6-894d-63758078328f, 64b79d25-6a78-49a8-af13-7323d650548e, ab4e3476-c982-4a06-865e-1cbe35bef7cb]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c976cd19-9b97-4ba5-8d9e-cfd2adec3bd1
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=972, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 64b79d25-6a78-49a8-af13-7323d650548e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [189a9c5d-5aa3-4564-bdec-db0368c93cbe]
name                : eth22

_uuid               : ab4e3476-c982-4a06-865e-1cbe35bef7cb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2700f4b0-7650-4c3e-bfd7-65c38ec459c0]
name                : eth23

_uuid               : 592737e6-37fc-44e6-894d-63758078328f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c700e88c-e53f-4102-94df-adcc50c3b206]
name                : eth21

_uuid               : 2fa21197-cbed-431f-9435-c5ece9e2e98c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a6e869e0-0989-4d58-9cc2-6fc00e197274]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c700e88c-e53f-4102-94df-adcc50c3b206
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
statistics          : {collisions=0, rx_bytes=1729938392, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26995871, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a6e869e0-0989-4d58-9cc2-6fc00e197274
admin_state         : down
duplex              : full
ifindex             : 458
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

_uuid               : 2700f4b0-7650-4c3e-bfd7-65c38ec459c0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2361737908, tx_dropped=0, tx_errors=0, tx_packets=7301115}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 189a9c5d-5aa3-4564-bdec-db0368c93cbe
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1903873992, tx_dropped=0, tx_errors=0, tx_packets=12749478}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fa42f4f849eeb1d2ea0506ff56e286451d73faf2
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Thu Jun 12 14:30:47 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jun 12 11:22:05 2014 -0700

    connmgr: Do not use OFPRR_METER_DELETE before OF1.4
    
    OFPRR_METER_DELETE was introduced in OF1.4 however meters were introduced
    in OF1.3.
    
    Regardless of the OF version when flows are deleted cause flows to be
    deleted handle_delete_meter&#40;&#41; calls delete_flows__&#40;&#41; with
    OFPRR_METER_DELETE as the reason.
    
    In order to avoid sending OFPRR_METER_DELETE to controllers connected
    using OF1.3 map OFPRR_METER_DELETE to OFPRR_DELETE which exists in that
    version.
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
