---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
694c3a44-e639-4d0f-bdee-448500d4c81d
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c054d6d3-5ed4-487e-a31a-144e8018b04b
controller          : [823742ab-438b-40c1-8dcc-07eedec37aef]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0dfbf8c6-a904-4e79-9105-e7a75908119a, 37e0383f-1aa3-4d3e-8dae-a0f8e68f9aa4, a4dee0fd-086a-4cb8-bebc-d4b6e625bf16, b01eb3d7-2a4d-492d-81a1-a91c3165ea60]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 823742ab-438b-40c1-8dcc-07eedec37aef
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=981, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a4dee0fd-086a-4cb8-bebc-d4b6e625bf16
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a37ae0a5-158a-475c-b573-780f4a417d6f]
name                : br0

_uuid               : 0dfbf8c6-a904-4e79-9105-e7a75908119a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dcb7a9ca-3102-42f0-8da0-725714f6fa4c]
name                : eth23

_uuid               : b01eb3d7-2a4d-492d-81a1-a91c3165ea60
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [20f122ff-dc07-4f25-a6f9-6cde3738d137]
name                : eth21

_uuid               : 37e0383f-1aa3-4d3e-8dae-a0f8e68f9aa4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [27d29422-fd97-41a3-b015-78de0cbe7e3f]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a37ae0a5-158a-475c-b573-780f4a417d6f
admin_state         : down
duplex              : full
ifindex             : 670
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

_uuid               : 27d29422-fd97-41a3-b015-78de0cbe7e3f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1770530202, tx_dropped=0, tx_errors=0, tx_packets=35588854}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : dcb7a9ca-3102-42f0-8da0-725714f6fa4c
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=424403784, tx_dropped=0, tx_errors=0, tx_packets=11736866}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 20f122ff-dc07-4f25-a6f9-6cde3738d137
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
statistics          : {collisions=0, rx_bytes=2168771104, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=90335069, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
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
