---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
91dc844e-11e4-4f2a-af25-b68c0ab84305
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 62d18ff6-aaf2-40dc-825b-dba9a3e45141
controller          : [a29da379-8494-4ec4-9476-f61597dc2a8d]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2391a5dd-a97e-4f3c-b08e-8a076cf392c1, 5c9631ab-4939-4716-bada-2e277cb60f68, 7ee6197b-b53c-49de-b4ea-5a4ac7df16a6, b9b79992-3f5b-4682-9a93-af4512a8a3be]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a29da379-8494-4ec4-9476-f61597dc2a8d
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=977, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2391a5dd-a97e-4f3c-b08e-8a076cf392c1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dd1ea04c-0f41-4684-93bf-c8ca951706a5]
name                : br0

_uuid               : b9b79992-3f5b-4682-9a93-af4512a8a3be
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0bb810b0-b2dc-4e1b-a64c-a8a0512f4fa2]
name                : eth21

_uuid               : 5c9631ab-4939-4716-bada-2e277cb60f68
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b973abcf-cb05-413c-a4e6-31d6ae696013]
name                : eth23

_uuid               : 7ee6197b-b53c-49de-b4ea-5a4ac7df16a6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [15c8b225-4b80-43c7-b041-372c2fd3da4c]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : dd1ea04c-0f41-4684-93bf-c8ca951706a5
admin_state         : down
ifindex             : 672
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

_uuid               : 0bb810b0-b2dc-4e1b-a64c-a8a0512f4fa2
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
statistics          : {collisions=0, rx_bytes=2285672600, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=90413634, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 15c8b225-4b80-43c7-b041-372c2fd3da4c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1811368036, tx_dropped=0, tx_errors=0, tx_packets=35616311}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b973abcf-cb05-413c-a4e6-31d6ae696013
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=523820784, tx_dropped=0, tx_errors=0, tx_packets=11803144}
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
