---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
bbdb0d43-436b-4ad7-973d-4ecd15d1d13d
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 6953110f-7af2-423e-bab1-3db789c96019
controller          : [a9981d57-4c25-45fe-9e17-5cf77e1331bc]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [99176134-cf99-499c-b535-b453ad4a6f29, c1e43f82-a98a-4c52-ae5c-ddc7dcb669d4, e80fb504-4b33-4b76-9812-5235bd7bd840]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a9981d57-4c25-45fe-9e17-5cf77e1331bc
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=382, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 99176134-cf99-499c-b535-b453ad4a6f29
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9126e773-0631-469e-85f6-7e2abb37bf25]
name                : br0

_uuid               : e80fb504-4b33-4b76-9812-5235bd7bd840
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7297d99c-0180-458b-823e-2a866fef40e6]
name                : eth7

_uuid               : c1e43f82-a98a-4c52-ae5c-ddc7dcb669d4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4a1c70f7-42c7-413b-8a45-68cb0dea439c]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7297d99c-0180-458b-823e-2a866fef40e6
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
statistics          : {collisions=0, rx_bytes=3068840602, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72691834, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 9126e773-0631-469e-85f6-7e2abb37bf25
admin_state         : up
duplex              : full
ifindex             : 716
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

_uuid               : 4a1c70f7-42c7-413b-8a45-68cb0dea439c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5357200, tx_dropped=0, tx_errors=0, tx_packets=57115}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit b8da6cce47501f003c9791054a59a5a6632e4c2c
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Mon Mar 24 21:10:39 2014 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Mon Mar 24 23:00:56 2014 -0700

    dpif-netdev: Fix a compilation warning
    
    Building OVS tree without DPDK produced the following warning message:
        lib/dpif-netdev.c:1868:5: error: statement with no effect
    
    This error message is complaining the return value of the following
    macro not being used.
    	#define pmd_thread_setaffinity_cpu(c) (0)
    
    The patch fixed this warnning by making the stub functions
    as inline funtions.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
