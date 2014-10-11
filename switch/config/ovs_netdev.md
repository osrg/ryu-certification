---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
07e168af-078c-4973-921a-138f5e26b641
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 1d047dcd-56cd-41a5-a1fc-6fd3f3058385
controller          : [cbb7f8c1-dfff-4a5a-a230-2d1705ec8d07]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [7c740a6d-8aa7-4d97-880b-63ff70c85678, 8ba8c0a1-fc64-4ee0-aa75-4a2cf145de9c, acc24163-3cde-44f0-8f32-74beff229cef, c768a01c-80ef-4bb5-a31d-eb1337c1a4ce]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : cbb7f8c1-dfff-4a5a-a230-2d1705ec8d07
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=707, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c768a01c-80ef-4bb5-a31d-eb1337c1a4ce
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [86d25a46-fd65-4a3f-9401-55989e45b0e2]
name                : eth22

_uuid               : 7c740a6d-8aa7-4d97-880b-63ff70c85678
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f6cf3db4-90a7-430b-a788-16a1a0284816]
name                : eth23

_uuid               : 8ba8c0a1-fc64-4ee0-aa75-4a2cf145de9c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [200a51da-98b4-46ce-ac1b-5fe1aa9b1fb8]
name                : eth21

_uuid               : acc24163-3cde-44f0-8f32-74beff229cef
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cac8aa5c-1521-49d2-8808-ce54ff51beb3]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : cac8aa5c-1521-49d2-8808-ce54ff51beb3
admin_state         : down
duplex              : full
ifindex             : 236
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

_uuid               : f6cf3db4-90a7-430b-a788-16a1a0284816
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1781314408, tx_dropped=0, tx_errors=0, tx_packets=6914166}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 86d25a46-fd65-4a3f-9401-55989e45b0e2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2229417454, tx_dropped=0, tx_errors=0, tx_packets=98875198}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 200a51da-98b4-46ce-ac1b-5fe1aa9b1fb8
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
statistics          : {collisions=0, rx_bytes=1543741033, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=161455604, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ff601a08a44c37fa8a6e0e569dc00d6731f55555
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Fri Oct 10 14:41:10 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Fri Oct 10 16:07:32 2014 -0700

    ofproto-dpif-upcall: Fix out-of-scope use of stack memory.
    
    Commit cc377352d &#40;ofproto: Reorganize in preparation for direct
    dpdk upcalls.&#41; introduced the bug that keeps reference to 'struct
    flow' defined on the stack inside while loop when running out of
    the scope.  This causes strange bug like wrong mask extraction
    when the part of memory is corrupted, and could lead to even
    more serious bug/crash.
    
    This commit fixes the above issue by defining an array of the
    'struct flow's on the function stack.
    
    Found by running ovs on RHEL7.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
