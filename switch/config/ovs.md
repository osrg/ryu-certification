---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b79e81f1-eb3a-460a-ac1b-85a5fcf2a185
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 79b2c25d-e4dd-49d3-8355-79009a21d912
controller          : [6af052c4-8ff0-4e86-bf52-98e07d263dad]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [28b7e992-bd74-454d-8482-0b613e55d1de, 5bb3db27-9e07-4379-bf74-398d6b1e5961, abe0b514-7996-4011-b153-21fef15ffa26, c9870b8e-4664-42d5-a8a4-21da978ca7cf]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6af052c4-8ff0-4e86-bf52-98e07d263dad
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=981, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : abe0b514-7996-4011-b153-21fef15ffa26
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c60569d2-e31e-449f-8f60-ea281950562e]
name                : eth22

_uuid               : 28b7e992-bd74-454d-8482-0b613e55d1de
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [602196a8-9de0-4153-880a-959183f66e73]
name                : eth23

_uuid               : c9870b8e-4664-42d5-a8a4-21da978ca7cf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ded9197a-ac75-4f77-b6f0-2487e01682ca]
name                : eth21

_uuid               : 5bb3db27-9e07-4379-bf74-398d6b1e5961
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f3daab6e-941f-455b-911e-0f17da47999a]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 602196a8-9de0-4153-880a-959183f66e73
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=126127284, tx_dropped=0, tx_errors=0, tx_packets=11538015}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ded9197a-ac75-4f77-b6f0-2487e01682ca
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
statistics          : {collisions=0, rx_bytes=1818026116, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=90099347, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c60569d2-e31e-449f-8f60-ea281950562e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1647983700, tx_dropped=0, tx_errors=0, tx_packets=35506461}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f3daab6e-941f-455b-911e-0f17da47999a
admin_state         : down
ifindex             : 664
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 2b651e449bb0005403e7a0474d56be2752567f4f
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Jun 24 16:39:33 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Jun 24 17:12:22 2014 -0700

    dpif: When executing actions needs help, use &quot;set&quot; action to set tunnel.
    
    Open vSwitch userspace is able to implement some actions that the kernel
    doesn't support, such as modifying ARP fields.  When it does this for a
    tunneled packet, it needs to supply the tunnel information with a &quot;set&quot;
    action, because the Linux kernel datapath throws away tunnel information
    supplied in the OVS_PACKET_CMD_EXECUTE metadata argument.
    
    VMware-BZ: #1270110
    Reported-by: Srinivas Neginhal &lt;sneginha@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
