---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
896e53ac-0d47-488f-9802-d2a8020e8d45
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
_uuid               : 83e5107a-9648-4e86-aedf-50e0cf9ccaa2
controller          : [a560f8b6-3c32-4bac-83cb-f344a2e70311]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [07c923f6-ff88-43cd-98d2-1e446ee2e7ba, 2e5a644d-05c4-467a-ac54-56302b92d0ec, 47903713-5016-48e8-b832-43c5c09d30da]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a560f8b6-3c32-4bac-83cb-f344a2e70311
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=351, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2e5a644d-05c4-467a-ac54-56302b92d0ec
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [01869c07-8561-4a07-bca5-a7313d1ca87a]
name                : eth7

_uuid               : 07c923f6-ff88-43cd-98d2-1e446ee2e7ba
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [60559776-688a-4602-a15e-b00bcc727f0c]
name                : eth8

_uuid               : 47903713-5016-48e8-b832-43c5c09d30da
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4e34319e-2318-4f3b-948b-5fa09a448f1d]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 60559776-688a-4602-a15e-b00bcc727f0c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 4e34319e-2318-4f3b-948b-5fa09a448f1d
admin_state         : up
ifindex             : 121
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 01869c07-8561-4a07-bca5-a7313d1ca87a
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
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c3b758f6fe8b7ae5e3e0204236f6aba48d714bc1
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Dec 5 16:59:13 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Jan 21 09:55:30 2014 -0800

    vlog: Avoid deadlock in vlog_init__() corner case.
    
    Anything inside vlog_init__() that tried to log a message was going to
    deadlock, since it would hit pthread_once() recursively and wait for the
    previous call to complete.  Unfortunately, there was a VLOG_ERR call inside
    vlog_init__(), only called in the corner case where the system's clock was
    wrong.
    
    This fixes the problem by rearranging code so that the logging isn't
    inside the once-only region.
    
    Found by inspection.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
