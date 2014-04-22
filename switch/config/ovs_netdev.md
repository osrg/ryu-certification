---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6bd20fe8-dccd-403d-87c4-620d7f35c674
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 42049156-a6fb-41ff-8bae-46e5c1bb89cb
controller          : [6e734fad-ace2-46d2-8f15-b71c3f040e2c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [40e226a6-c8d5-40f5-950e-fcd037488cf6, 99275ae1-c819-4266-9d55-8be6ad696239, d8dbc356-4c4c-4f87-9a4a-4c8d5f806fa4, e9c0de88-1dce-44e6-bbbc-86e4ce5f8546]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6e734fad-ace2-46d2-8f15-b71c3f040e2c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=571, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e9c0de88-1dce-44e6-bbbc-86e4ce5f8546
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c6eea931-286e-41c0-9b5f-b1f5131ea428]
name                : eth22

_uuid               : 99275ae1-c819-4266-9d55-8be6ad696239
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dbb97549-61ef-4c2f-ac9a-ad4c1e5fb7f5]
name                : eth21

_uuid               : 40e226a6-c8d5-40f5-950e-fcd037488cf6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [188c2fbb-fde5-45ce-909d-b49a20eb8b6d]
name                : eth23

_uuid               : d8dbc356-4c4c-4f87-9a4a-4c8d5f806fa4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fbdcffa2-23a6-4418-9501-069c92c09baf]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : dbb97549-61ef-4c2f-ac9a-ad4c1e5fb7f5
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
statistics          : {collisions=0, rx_bytes=421466764, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=285561, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c6eea931-286e-41c0-9b5f-b1f5131ea428
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=272866442, tx_dropped=0, tx_errors=0, tx_packets=183614}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : fbdcffa2-23a6-4418-9501-069c92c09baf
admin_state         : down
duplex              : full
ifindex             : 1062
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

_uuid               : 188c2fbb-fde5-45ce-909d-b49a20eb8b6d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=218496000, tx_dropped=0, tx_errors=0, tx_packets=145664}
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
