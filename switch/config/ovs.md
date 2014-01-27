---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3365772b-678e-414a-b14d-4ac4b29264c2
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 2e0082eb-42a4-4bd3-b4b1-1900cd7e24a5
controller          : [6ac3021f-6d19-4721-905c-ad167f5c8547]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0a394c4d-b780-4e46-99d9-23aa0e17d7f7, 2714db50-7cff-4fc6-8b23-5873599255f6, 74bd1b90-11db-4c0c-ae80-469ce72eaf35]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6ac3021f-6d19-4721-905c-ad167f5c8547
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2714db50-7cff-4fc6-8b23-5873599255f6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [185fd69d-c83f-4f63-ba8b-c49a1e2a1108]
name                : eth7

_uuid               : 74bd1b90-11db-4c0c-ae80-469ce72eaf35
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [73a8ce0c-f265-46ca-8afc-d02588742b68]
name                : br0

_uuid               : 0a394c4d-b780-4e46-99d9-23aa0e17d7f7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1e5ce059-d6ef-44ee-a6e6-6f0237494cc8]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 73a8ce0c-f265-46ca-8afc-d02588742b68
admin_state         : up
ifindex             : 77
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

_uuid               : 185fd69d-c83f-4f63-ba8b-c49a1e2a1108
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

_uuid               : 1e5ce059-d6ef-44ee-a6e6-6f0237494cc8
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
commit 9d0581fdf22bec79fc09cddb29808c89d16f0266
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Mon Jan 27 08:52:57 2014 -0800
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Mon Jan 27 10:33:45 2014 -0800

    getopt_long: Copy over the implementation from netbsd.
    
    Windows does not have a getopt_long function. This commit
    copies over the getopt_long implementation from netbsd with
    some minor modifications and is used only on Windows platform.
    
    Modifications on top of the version in NetBSD repo.
    * Remove header files not available in Visual Studio.
    * Remove some unwanted #defines.
    * Add Open vSwitch specific header files like config.h, vlog.h, util.h
    * Add the following #define's
    define __UNCONST(a)    ((void *)(unsigned long)(const void *)(a))
    define _DIAGASSERT(q) ovs_assert(q)
    define warnx VLOG_WARN
    * Add extern declaration in getopt.h for optarg, optind.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
