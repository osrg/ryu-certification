---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
19625ab0-7837-4ce5-9278-9558d3e3b7e2
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
_uuid               : 2057f220-c6db-4c4e-932c-c3102bc6bf38
controller          : [f74fd4f3-a49a-4661-bc48-cf9afa785342]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [8526b20e-fe09-4c4e-b497-e1b346b2b790, c64d3d67-d4ad-4063-9fc4-04bd305409fa, f9ebea73-37b5-40af-90b7-c499dcff90c1]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f74fd4f3-a49a-4661-bc48-cf9afa785342
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=297, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8526b20e-fe09-4c4e-b497-e1b346b2b790
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d7037f8f-072b-403d-9601-fec49fdf497c]
name                : eth7

_uuid               : c64d3d67-d4ad-4063-9fc4-04bd305409fa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [edb82a55-d2f3-4f26-9975-855f9544bd1e]
name                : eth8

_uuid               : f9ebea73-37b5-40af-90b7-c499dcff90c1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [618d2aa6-b062-42c7-a4d5-51d3183cdae0]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : edb82a55-d2f3-4f26-9975-855f9544bd1e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1809242, tx_dropped=0, tx_errors=0, tx_packets=19325}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 618d2aa6-b062-42c7-a4d5-51d3183cdae0
admin_state         : up
duplex              : full
ifindex             : 236
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

_uuid               : d7037f8f-072b-403d-9601-fec49fdf497c
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
statistics          : {collisions=0, rx_bytes=3056954134, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72571320, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f1c8a79c626f383926b70eb1885c40f8a427ba23
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Thu Feb 6 15:46:05 2014 -0800
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Tue Feb 11 11:48:29 2014 -0800

    bond: Change the way of assigning bond slave for unassigned bond entry.
    
    Before this commit, ovs randomly selects a slave for unassigned
    bond entry.  If the selected slave is not enabled, the active slave
    is chosen instead.  In this commit, the slave is selected from the
    list of all enabled slaves in a round-robin fashion.  This helps
    improve the consistency of bond behavior when new flows are added.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
