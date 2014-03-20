---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9e61da2a-9ebf-406e-a82a-3a5a9a5ed563
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
_uuid               : 81d4f925-97a1-44da-a55b-01daf4da6063
controller          : [c3736224-49fa-4714-8863-224900d09e07]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [224087f9-c352-45db-a590-e4e46e1606c3, 5fad0948-73c3-49b4-84f5-0419dd08c381, f738b903-7210-46fe-8de9-cad161231718]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c3736224-49fa-4714-8863-224900d09e07
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=382, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5fad0948-73c3-49b4-84f5-0419dd08c381
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6229486a-4c39-4625-9a8c-550c3377996c]
name                : eth8

_uuid               : 224087f9-c352-45db-a590-e4e46e1606c3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1f87b7e9-875d-4c8c-b0a0-3359736ba311]
name                : eth7

_uuid               : f738b903-7210-46fe-8de9-cad161231718
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c4159bd7-89b3-432a-99ba-967da391d2e0]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1f87b7e9-875d-4c8c-b0a0-3359736ba311
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
statistics          : {collisions=0, rx_bytes=3067001098, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72673163, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 6229486a-4c39-4625-9a8c-550c3377996c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4813686, tx_dropped=0, tx_errors=0, tx_packets=51328}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : c4159bd7-89b3-432a-99ba-967da391d2e0
admin_state         : up
duplex              : full
ifindex             : 650
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 63be20bee256f305801c0674b29e5773355d2379
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Wed Feb 26 10:07:38 2014 -0800
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Thu Mar 20 10:27:20 2014 -0700

    dpif-netdev: Implement the API functions to allow multiple handler
    threads read upcall.
    
    This commit implements the API functions to allow multiple handler
    threads read upcall.
    
    Also, this commit removes the handling priority of DPIF_UC_MISS
    over DPIF_UC_ACTION.  So, both misses will be put to the same
    queue.  The decision is based on the fact that a lot has changed
    since the age when flow setup rate is most treasured and starving
    all actions in the presence of any flow misses doesn't seem like
    a sound balancing solution.
    
    Thusly the current implementation will be put in testing and
    investigation for better balancing solution will continue if
    there is an issue.
    
    Also note, the introduction and use of flow_hash_5tuple() will
    put missed ICMP packets from same source but with different
    type/code to different handler queues.  This may cause reordering
    of these packets.  For now, we do not count this as a problem.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
