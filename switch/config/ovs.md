---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
31eb9cb2-6e8a-4c8a-a3ea-eed18fe1e4ff
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
_uuid               : ffa48229-cac1-4b55-82d9-8d174efe4b3f
controller          : [58a06c33-55f7-4f7e-a623-d696c44c0328]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4480d79f-c5ce-4438-a384-698ca0b80d6e, a5c926aa-9d66-4d20-ac2d-0cbab2461b81, b21e98d9-1e21-4d0b-b403-fa2781b1940b, d6d13919-3fab-49e2-aa76-138e10d29687]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 58a06c33-55f7-4f7e-a623-d696c44c0328
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=10, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d6d13919-3fab-49e2-aa76-138e10d29687
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8bf31fe1-f2ac-46f7-a4ac-441599f9c2b6]
name                : br0

_uuid               : b21e98d9-1e21-4d0b-b403-fa2781b1940b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bbdcbde2-167d-40d8-9fa8-50458f46212a]
name                : eth21

_uuid               : a5c926aa-9d66-4d20-ac2d-0cbab2461b81
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f19855d4-7952-4b5e-9352-0d52d4a6983d]
name                : eth23

_uuid               : 4480d79f-c5ce-4438-a384-698ca0b80d6e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6a568de3-f291-4011-9e31-b37d3caa9b97]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f19855d4-7952-4b5e-9352-0d52d4a6983d
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1500
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8bf31fe1-f2ac-46f7-a4ac-441599f9c2b6
admin_state         : down
ifindex             : 1068
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : bbdcbde2-167d-40d8-9fa8-50458f46212a
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=61439, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=663, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6a568de3-f291-4011-9e31-b37d3caa9b97
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1500
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18820, tx_dropped=0, tx_errors=0, tx_packets=201}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1f8675481e8cc976931bd0a85851d780f7cf2a33
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Mon Apr 21 17:31:11 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Mon Apr 21 18:44:09 2014 -0700

    ofproto-dpif-upcall: Fix ovs-vswitchd crash.
    
    On current master, caller of udpif_set_threads&#40;&#41; can pass 0 value
    on n_handlers and n_revalidators to delete all handler and revalidator
    threads.
    
    After commit 9a159f748866 &#40;ofproto-dpif-upcall: Remove the dispatcher
    thread.&#41;, udpif_set_threads&#40;&#41; also calls the dpif_handlers_set&#40;&#41; with
    the 0 value 'n_handlers'.  Since dpif level always assume the 'n_handlers'
    be non-zero, this causes warnings and even crash of ovs-vswitchd.
    
    This commit fixes the above issue by defining separate functions for
    starting and stopping handler and revalidator threads.  So
    udpif_set_threads&#40;&#41; will never be called with 0 value arguments.
    
    Reported-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Co-authored-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
