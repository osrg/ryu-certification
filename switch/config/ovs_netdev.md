---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e9c2607a-45aa-43f0-9fb8-dd320a328600
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 699b28e6-5d7a-46e9-8a9d-169d960ec7de
controller          : [95a1c44f-ccdd-42bc-83be-f86896ad9d46]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0cd5428f-f275-485b-a108-33edba1d7a52, 3476f5f5-afa1-450b-9520-7e960bf5c025, 68805814-5729-4839-8e8d-db86eed06615]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 95a1c44f-ccdd-42bc-83be-f86896ad9d46
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=942, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 68805814-5729-4839-8e8d-db86eed06615
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b9a14072-f544-426a-923f-b43e8523d844]
name                : eth7

_uuid               : 3476f5f5-afa1-450b-9520-7e960bf5c025
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2412756e-ca62-451f-bf40-5bd43d596d30]
name                : br0

_uuid               : 0cd5428f-f275-485b-a108-33edba1d7a52
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a817fbab-6a96-4036-8978-efe8a69b4572]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2412756e-ca62-451f-bf40-5bd43d596d30
admin_state         : down
duplex              : full
ifindex             : 927
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : b9a14072-f544-426a-923f-b43e8523d844
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
statistics          : {collisions=0, rx_bytes=3074460432, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72748871, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : a817fbab-6a96-4036-8978-efe8a69b4572
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7028787, tx_dropped=0, tx_errors=0, tx_packets=74921}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a5b8d49bc61cf6d7ad2277f08aea05dd25eaca4c
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Apr 8 15:39:18 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Apr 8 15:39:18 2014 -0700

    datapath: Fix tracking of flags seen in TCP flows.
    
    Flow statistics need to take into account the TCP flags from the packet
    currently being processed (in 'key'), not the TCP flags matched by the
    flow found in the kernel flow table (in 'flow').
    
    This bug made the Open vSwitch userspace fin_timeout action have no effect
    in many cases.
    
    Bug #1219516.
    Reported-by: Len Gao &lt;leng@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
