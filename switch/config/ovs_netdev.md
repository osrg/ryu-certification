---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e4105c6d-987f-43f8-a259-dfd1961e6c53
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7fce807c-afab-4480-b87e-9f0ef57f7a47
controller          : [ffd8447b-4888-4106-a4c2-2adb41b52eaa]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0029bae4-1fa8-4c91-a7e5-0e87912a2d11, 0d437689-e5e1-4055-bef5-bf5bb8ae8202, 616c84a6-99c1-4acd-8454-d00077ece824, b54e91c9-6391-4a24-8ed5-e92b4aab3c5f]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ffd8447b-4888-4106-a4c2-2adb41b52eaa
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=562, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0029bae4-1fa8-4c91-a7e5-0e87912a2d11
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [235f4b31-8430-43a1-a905-6f6a07caae13]
name                : eth22

_uuid               : 0d437689-e5e1-4055-bef5-bf5bb8ae8202
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0f7d9ec5-2668-4b45-babb-8ae73453067d]
name                : eth23

_uuid               : b54e91c9-6391-4a24-8ed5-e92b4aab3c5f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [20649f54-b6e4-418e-8c81-5645e248ff80]
name                : br0

_uuid               : 616c84a6-99c1-4acd-8454-d00077ece824
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [87ea6b70-729b-452c-af4a-9a29736021c8]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 87ea6b70-729b-452c-af4a-9a29736021c8
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
statistics          : {collisions=0, rx_bytes=2524355814, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1689967, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 20649f54-b6e4-418e-8c81-5645e248ff80
admin_state         : down
duplex              : full
ifindex             : 97
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

_uuid               : 0f7d9ec5-2668-4b45-babb-8ae73453067d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1817781000, tx_dropped=0, tx_errors=0, tx_packets=1211854}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 235f4b31-8430-43a1-a905-6f6a07caae13
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=963486164, tx_dropped=0, tx_errors=0, tx_packets=644980}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ac64794acb85a28059c666ef99250971880027b3
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue May 20 11:37:02 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue May 20 11:37:02 2014 -0700

    dpif: Refactor flow dumping interface to make better sense for batching.
    
    Commit a6ce4b9d251 &#40;ofproto-dpif-upcall: Avoid use-after-free in
    revalidate&#40;&#41; corner case.&#41; showed that it is somewhat tricky to correctly
    use the existing dpif flow dumping interface to obtain batches of flows.
    One has to be careful about calling dpif_flow_dump_next_may_destroy_keys&#40;&#41;
    before going on to the next flow.
    
    A better interface is possible, one that is naturally oriented toward
    retrieving batches when that is a useful optimization.  This commit
    replaces the dpif interface by such a design, and updates both the
    implementations and the callers to adopt it.
    
    This is a fairly large change, but I think that the code in
    ofproto-dpif-upcall is easier to understand after the change.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
