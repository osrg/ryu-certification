---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
957ef4e5-198b-4d8f-acb5-afcf5f50e70d
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ef68919e-6cb9-4092-b776-83b7c4a3c1a7
controller          : [f3370382-36cf-4691-9416-bdbcb3cf8ada]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [41ba74df-71aa-497a-ab62-942f6d8cbc87, c43e1d42-49dd-4de3-a2b5-28e957f6b156, c503fba4-d261-4a5f-b8bd-69dba412a55d]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f3370382-36cf-4691-9416-bdbcb3cf8ada
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=922, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c503fba4-d261-4a5f-b8bd-69dba412a55d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [26774254-1ff5-421c-ba3a-d1c0eecbd8a3]
name                : eth8

_uuid               : c43e1d42-49dd-4de3-a2b5-28e957f6b156
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aeb15bfd-0145-4de1-b9e8-8867309e3a2f]
name                : br0

_uuid               : 41ba74df-71aa-497a-ab62-942f6d8cbc87
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e2cd56c5-34c6-4683-a288-75765dc6db54]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 26774254-1ff5-421c-ba3a-d1c0eecbd8a3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7143441, tx_dropped=0, tx_errors=0, tx_packets=76143}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : aeb15bfd-0145-4de1-b9e8-8867309e3a2f
admin_state         : down
duplex              : full
ifindex             : 944
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

_uuid               : e2cd56c5-34c6-4683-a288-75765dc6db54
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
statistics          : {collisions=0, rx_bytes=3074847164, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72752801, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ce58df5be1933ff218aa8f892394756892f0e85c
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Wed Apr 9 11:13:57 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Wed Apr 9 11:38:11 2014 -0700

    Tests: Fix ofproto/trace and expose megaflows when having a set action.
    
    ofproto/trace incorrectly reported the megaflow based on the modified
    flow, rather than the original flow key.  Now the original flow key is
    stored before any modifications and is used for reporting the megaflow.
    
    Also, flow reporting is suppressed only for resubmit flows, so that
    the final flow will be printed if it is different from the incoming
    flow key.
    
    Test for the megaflow key and mask with flows having set actions.
    This helps in verifying the correctness of operation with masked set
    actions in the following patches.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
