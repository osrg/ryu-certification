---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
214208f6-7635-4dca-8e85-9b46ce555856
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : dc62df4f-c97e-48f4-a113-025d49dcd711
controller          : [2ec1c08c-5fc8-4918-a37f-ab243da3b760]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [41f3253b-08ba-4eb8-9a04-484fd0879148, 636c0cf2-a4f1-4088-a565-1d2ae1b5d1d5, f8e74d0f-c175-4e54-9461-dfeb14ccc1bd]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2ec1c08c-5fc8-4918-a37f-ab243da3b760
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=371, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 636c0cf2-a4f1-4088-a565-1d2ae1b5d1d5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [551304f4-7fdf-43af-aa3a-ceadbbe47026]
name                : eth7

_uuid               : f8e74d0f-c175-4e54-9461-dfeb14ccc1bd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fd0ec4f3-1659-40eb-8bf0-c7e14fba2f00]
name                : br0

_uuid               : 41f3253b-08ba-4eb8-9a04-484fd0879148
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1ca72ebf-c9a1-4ed8-b073-44f80e12d80f]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 551304f4-7fdf-43af-aa3a-ceadbbe47026
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
statistics          : {collisions=0, rx_bytes=3059865681, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72600756, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 1ca72ebf-c9a1-4ed8-b073-44f80e12d80f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2717264, tx_dropped=0, tx_errors=0, tx_packets=29005}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : fd0ec4f3-1659-40eb-8bf0-c7e14fba2f00
admin_state         : up
duplex              : full
ifindex             : 342
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
commit 3f142f59f2859ef5c2bc124405ab4d683d3f416b
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Feb 25 08:01:01 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Feb 25 08:01:01 2014 -0800

    ofproto-dpif: Complete all packet translations before freeing an ofproto.
    
    The following scenario can occur:
    
       1. Handler thread grabs a pointer to an ofproto in handle_upcalls().
    
       2. Main thread removes ofproto and destroys it in destruct().
    
       3. Handler thread uses pointer to ofproto and accesses freed memory.
          BOOM!
    
    Each individual step above happens under the xlate_rwlock, but the ofproto
    pointer is retained from step 1 to step 3, hence the problem.  This commit
    fixes the problem by ensuring that after an ofproto is removed but before
    it is destroyed, all packet translations get pushed all the way through
    the upcall handler pipeline.  (No new packet translations can get a pointer
    to the removed ofproto.)
    
    Bug #1200351.
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
