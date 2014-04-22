---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
661e5530-45f5-4998-a97a-4c6071cd1839
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
_uuid               : 5f1d275f-619e-4c69-8057-224e3a036948
controller          : [83ebe26c-49ab-42fa-8922-35111dbec611]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [31be4712-feff-44ed-9e9f-35c83d7b0367, 49b1f89d-8fe7-4cc3-9d4c-9d5fcb027e5e, 8cc88cfb-f6d4-4663-819e-8f16533ec98a, bfdc919a-e9ec-4915-bbef-b030db66da8e]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 83ebe26c-49ab-42fa-8922-35111dbec611
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=572, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 49b1f89d-8fe7-4cc3-9d4c-9d5fcb027e5e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b009d56a-a3ef-479a-8c84-00cf4cddd1b6]
name                : eth21

_uuid               : 31be4712-feff-44ed-9e9f-35c83d7b0367
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2b6dd2d3-6b96-42e6-b6d0-dc5579b4b72d]
name                : eth23

_uuid               : bfdc919a-e9ec-4915-bbef-b030db66da8e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [604402b5-d577-4fe0-b845-8859dc32e3bd]
name                : eth22

_uuid               : 8cc88cfb-f6d4-4663-819e-8f16533ec98a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [64590705-7d42-491f-a43e-2cb40c919c65]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 604402b5-d577-4fe0-b845-8859dc32e3bd
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=685136972, tx_dropped=0, tx_errors=0, tx_packets=461248}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 64590705-7d42-491f-a43e-2cb40c919c65
admin_state         : down
duplex              : full
ifindex             : 1081
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

_uuid               : b009d56a-a3ef-479a-8c84-00cf4cddd1b6
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
statistics          : {collisions=0, rx_bytes=1014215399, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=686741, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2b6dd2d3-6b96-42e6-b6d0-dc5579b4b72d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=437761500, tx_dropped=0, tx_errors=0, tx_packets=291841}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 882470607bdbaec5a1252f34cf97f4b4ef000d21
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Tue Apr 15 11:32:26 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Tue Apr 22 11:13:03 2014 -0700

    ovs-rcu: Name the ovsrcu_postpone_thread to 'urcu'.
    
    The ovs-rcu module adds a new thread for checking the grace period.
    Since the thread name is not set, it will inherit the name of the
    thread that creates it.  This makes the 'top' output quite confusing.
    
    This commit names the thread to 'urcu' for clarity.
    
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
