---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9de4132e-06fd-4da0-bbb1-25da9ec5f1f9
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f94de557-ac12-495a-9ac6-ce2c457034a8
controller          : [2f1a0b68-18e0-4825-890d-2fa1041026ea]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [93245aa3-b2a0-4990-a28d-91eaee2b9b2b, c25e2eef-25bd-43db-9836-8ed8f64298c3, dc95f35b-7b72-43a0-8687-a87374d7cfd7, f1626ed4-2e68-4703-90ee-095b8b4082bc]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2f1a0b68-18e0-4825-890d-2fa1041026ea
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=747, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f1626ed4-2e68-4703-90ee-095b8b4082bc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [86afbdfa-2d83-4feb-a07a-9c9d57faa6e7]
name                : eth23

_uuid               : 93245aa3-b2a0-4990-a28d-91eaee2b9b2b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f862a43b-9af0-4097-b6da-9341f681eb12]
name                : br0

_uuid               : dc95f35b-7b72-43a0-8687-a87374d7cfd7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6d6e4ed8-2e45-455e-8b18-189a59b24c97]
name                : eth21

_uuid               : c25e2eef-25bd-43db-9836-8ed8f64298c3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4ef8dd39-5e40-41c8-8a18-4be1ecd76caf]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6d6e4ed8-2e45-455e-8b18-189a59b24c97
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
statistics          : {collisions=0, rx_bytes=1139077539, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=83818838, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 4ef8dd39-5e40-41c8-8a18-4be1ecd76caf
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=902184856, tx_dropped=0, tx_errors=0, tx_packets=49287829}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 86afbdfa-2d83-4feb-a07a-9c9d57faa6e7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1902876000, tx_dropped=0, tx_errors=0, tx_packets=1268584}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f862a43b-9af0-4097-b6da-9341f681eb12
admin_state         : down
ifindex             : 61
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 222820c67cea17ed76024364dcdd08778d1232fc
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Jul 29 09:54:17 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Aug 4 14:32:55 2014 -0700

    tests: Turn off appctl poll_loop logging for long output.
    
    One of the VMware internal autobuilder builds failed due to extraneous
    logging in these tests of the form:
    
       2014-07-28T21:11:07Z|00001|poll_loop|INFO|wakeup due to [POLLIN] on fd 3
       &#40;...&#41; at lib/stream-fd-unix.c:124 &#40;93% CPU usage&#41;
    
    I think this must be because these tests have tons of output and so on a
    loaded machine it can take some CPU to pull it down.  We don't want to fail
    for that reason, so disable this logging.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Ansis Atteka &lt;aatteka@nicira.com&gt;
</pre>
