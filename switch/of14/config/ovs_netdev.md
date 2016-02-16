---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1d4f255f-236d-41b7-8a72-43df7892b44a
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 1a471d4c-3144-4b6f-9d34-ec1c895631f5
controller          : [b96b1389-3633-4d33-be67-b8cac46cda07]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1a417cf8-e4c6-470e-a930-cd3403e352b8, 7421aea4-e847-40a4-a9ce-136ac7c43e1f, 837b12df-1700-4e4e-94d6-0f669ea94e46, dbbe7b3e-69a6-4bfa-9028-8390bbb492f2]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b96b1389-3633-4d33-be67-b8cac46cda07
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7421aea4-e847-40a4-a9ce-136ac7c43e1f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bc98591d-c1af-496f-8632-fd92ece1c511]
name                : "br0"

_uuid               : 1a417cf8-e4c6-470e-a930-cd3403e352b8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2e00eabb-c811-4cfc-8499-cf92b2ac4f0b]
name                : "eth23"

_uuid               : dbbe7b3e-69a6-4bfa-9028-8390bbb492f2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d4021dfa-a3ac-41d0-8a37-7beb4d69c898]
name                : "eth22"

_uuid               : 837b12df-1700-4e4e-94d6-0f669ea94e46
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1ed5f761-ac17-4bd0-9971-6740808fc720]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1ed5f761-ac17-4bd0-9971-6740808fc720
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=46023497957, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30752443, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : bc98591d-c1af-496f-8632-fd92ece1c511
admin_state         : down
duplex              : full
ifindex             : 800
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : d4021dfa-a3ac-41d0-8a37-7beb4d69c898
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30909679695, tx_dropped=0, tx_errors=0, tx_packets=20638613}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 2e00eabb-c811-4cfc-8499-cf92b2ac4f0b
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9188097000, tx_dropped=0, tx_errors=0, tx_packets=6125398}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5e2e2f970a78dc135e3f5bb6e0081f1564ff9d44
Author:     Alin Serdean &lt;aserdean@cloudbasesolutions.com&gt;
AuthorDate: Thu Feb 11 02:30:32 2016 +0000
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Tue Feb 16 11:20:10 2016 -0800

    datapath-windows: Enable multiprocessor compilation on solution
    
    Visual Studio defines by default the maximum number of concurrent jobs.
    
    This patch allows the parallel built of the solution.
    
    Signed-off-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Acked-by: Sairam Venugopal &lt;vsairam@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
