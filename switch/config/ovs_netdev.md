---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2a870b99-174b-4a3e-9a85-753ef5bc9245
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
_uuid               : 38289c5c-bde5-43b2-9109-a7f89ba6105e
controller          : [a5433390-d32d-4c9d-9e44-0f529d77cbfd]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5b00c20a-a940-471b-956c-94bcb2a4cc57, 7aa3e648-07f0-4565-8ec0-af3921ec3a0c, a09e31e5-66f8-453b-9ba2-b6bd09f7d5f8]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a5433390-d32d-4c9d-9e44-0f529d77cbfd
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=311, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7aa3e648-07f0-4565-8ec0-af3921ec3a0c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [437e8f8e-0def-4e06-92e4-9770ce6a61e0]
name                : br0

_uuid               : a09e31e5-66f8-453b-9ba2-b6bd09f7d5f8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2aec50a4-3139-43a3-97f4-4567e40d063c]
name                : eth8

_uuid               : 5b00c20a-a940-471b-956c-94bcb2a4cc57
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c55c6d62-d3c9-483b-b1c8-5cd6b016f6c9]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2aec50a4-3139-43a3-97f4-4567e40d063c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5899176, tx_dropped=0, tx_errors=0, tx_packets=62884}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : c55c6d62-d3c9-483b-b1c8-5cd6b016f6c9
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
statistics          : {collisions=0, rx_bytes=3070653798, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72710209, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 437e8f8e-0def-4e06-92e4-9770ce6a61e0
admin_state         : up
duplex              : full
ifindex             : 771
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
commit 5878877a75a11d9e73f61cebfa18ff84dcdd64ba
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Tue Mar 25 13:57:25 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Fri Mar 28 09:19:47 2014 -0700

    ofproto-dpif-upcall: Fix a race.
    
    Commit 61057e884ca9c(ofproto-dpif-upcall: Slightly simplify
    udpif_upcall_handler().) restructured the main loop in
    udpif_upcall_handler() and discarded the check for the
    'exit_latch' after acquiring the mutex.  This makes it
    possible for the following race:
    
    - main thread sets the 'exit_latch' after the handler thread
      checking it.
    - main thread acquires the handler thread mutex and signals the
      condition variable of handler thread.
    - main thread releases the mutex and 'join' the handler thread.
    - handler thread acquires the mutex, finds that n_upcalls is 0
      and waits on the signal of condition variable.
    - then OVS will hang forever.
    
    This commit fixes the above issue by adding a check for the
    'exit_latch' after acquiring the mutex.
    
    Bug #1217229
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
