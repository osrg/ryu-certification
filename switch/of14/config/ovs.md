---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7e8930aa-699d-41ac-a1fa-18358f978753
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
_uuid               : 512a6a68-d380-4c6f-958e-d814d9f521e7
controller          : [a40f243d-a16b-4153-a669-fcb0a1a847bd]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [05fc7bde-1fde-46eb-8e65-e18aebdebf1d, 2a43c965-189d-46c1-8b37-d74fa715f21b, 4f543ff9-0d81-4a6b-a985-26ba9836f428, f12d470d-f44a-4b64-a237-6240e3b7fd02]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a40f243d-a16b-4153-a669-fcb0a1a847bd
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=977, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4f543ff9-0d81-4a6b-a985-26ba9836f428
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [61b000bf-3046-4ce6-a35e-cd617bfe2ca6]
name                : eth22

_uuid               : 2a43c965-189d-46c1-8b37-d74fa715f21b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f45841de-b5cd-4f31-8a98-12443d403a48]
name                : br0

_uuid               : f12d470d-f44a-4b64-a237-6240e3b7fd02
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [35e7d293-1375-4a36-8a5f-86a2a0645285]
name                : eth21

_uuid               : 05fc7bde-1fde-46eb-8e65-e18aebdebf1d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [51676af6-ca1c-4a05-8557-cc1316813b83]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 51676af6-ca1c-4a05-8557-cc1316813b83
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=225382284, tx_dropped=0, tx_errors=0, tx_packets=11604185}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f45841de-b5cd-4f31-8a98-12443d403a48
admin_state         : down
ifindex             : 666
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

_uuid               : 35e7d293-1375-4a36-8a5f-86a2a0645285
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
statistics          : {collisions=0, rx_bytes=1934918612, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=90177906, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 61b000bf-3046-4ce6-a35e-cd617bfe2ca6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1688983534, tx_dropped=0, tx_errors=0, tx_packets=35534026}
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
