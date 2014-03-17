---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1f09b1f1-4646-4727-b34a-e56ecb3d14ff
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
_uuid               : 79c39fd7-8729-490a-be2d-690d5b023814
controller          : [ea99c699-59e0-4c40-a746-f1a77007605b]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [3ac6d829-ff9d-4f44-90c5-edf37ff58282, a1293c28-42a6-4559-89c4-9a9a4bbbaaee, efa21e79-0a1b-4db8-ac02-80be98999589]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ea99c699-59e0-4c40-a746-f1a77007605b
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=372, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a1293c28-42a6-4559-89c4-9a9a4bbbaaee
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [52926aaa-8323-4b51-b725-5d0ac45badaf]
name                : eth7

_uuid               : 3ac6d829-ff9d-4f44-90c5-edf37ff58282
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5abf3169-6ebf-4e5d-8410-87763a4409ca]
name                : br0

_uuid               : efa21e79-0a1b-4db8-ac02-80be98999589
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f2564e7f-985a-4021-bdfa-e178f64966b5]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 5abf3169-6ebf-4e5d-8410-87763a4409ca
admin_state         : up
duplex              : full
ifindex             : 555
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

_uuid               : 52926aaa-8323-4b51-b725-5d0ac45badaf
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
statistics          : {collisions=0, rx_bytes=3064935038, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72652191, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : f2564e7f-985a-4021-bdfa-e178f64966b5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4209296, tx_dropped=0, tx_errors=0, tx_packets=44892}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d0b99d38edaba6e744a5787b990e7b989684e179
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Thu Mar 13 15:28:54 2014 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Mon Mar 17 22:51:17 2014 -0700

    backtrace: Add log_backtrace()
    
    log_backtrace() and log_backtrace_msg() logs the back trace into
    the log file. It may be most useful when debugging unit tests.
    backtrace.h documents the usage. It is not being called directly
    in the code, but rather as a handy tool available when needed.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
