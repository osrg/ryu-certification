---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
dc617da5-7e0c-4083-aaf2-4b3f9901bd15
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 094e3564-987e-4e05-b0a7-de205f52cd1c
controller          : [299621f7-8ee6-4325-931e-99cae91b62a8]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [454b5e25-af32-4a29-a605-ff72030c6399, adedc6d3-305c-400f-b05d-d3c6be35d600, b2fa4d88-80ff-4d6c-bf42-e53432429a2d]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 299621f7-8ee6-4325-931e-99cae91b62a8
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=306, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b2fa4d88-80ff-4d6c-bf42-e53432429a2d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a7f4439d-59d2-46ae-858c-6cf9316ce7ee]
name                : br0

_uuid               : 454b5e25-af32-4a29-a605-ff72030c6399
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3b932f98-12a1-4512-8009-4388c9073cf4]
name                : eth7

_uuid               : adedc6d3-305c-400f-b05d-d3c6be35d600
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [22706c9f-c7fa-4403-bcb2-406da1dfc396]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3b932f98-12a1-4512-8009-4388c9073cf4
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
statistics          : {collisions=0, rx_bytes=3072163044, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72725526, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : a7f4439d-59d2-46ae-858c-6cf9316ce7ee
admin_state         : up
duplex              : full
ifindex             : 822
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

_uuid               : 22706c9f-c7fa-4403-bcb2-406da1dfc396
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6346566, tx_dropped=0, tx_errors=0, tx_packets=67649}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5fd2f418fa845b1aa8662a3d939af13b484af62c
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Fri Mar 28 15:15:02 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Mon Mar 31 09:03:46 2014 -0700

    util: xleep for Windows.
    
    Windows does not have a sleep(seconds). But it does have
    a Sleep(milliseconds). Sleep() in windows does not have a
    return value. Since we are not using the return value for xsleep()
    anywhere as of now, don't return any.
    
    Introduced by commit 275eebb9 (utils: Introduce xsleep for RCU quiescent state)
    
    CC: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
