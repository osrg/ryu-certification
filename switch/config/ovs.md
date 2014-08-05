---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e46c6766-da36-4769-a1f3-ac83dfe3206f
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
_uuid               : 7af9b4d4-4108-45b3-bab4-9868c128a0dc
controller          : [b6139016-94f4-460d-a4e7-8a4004e73f24]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [666c5190-3e16-47d8-9f59-aacea6ab4331, 780a2a2c-55a3-4aae-9466-d5df232e95e6, dc05fe81-b6c6-47fb-a33e-1e5c135546b1, e9a733b7-e855-41fd-ad21-13aeec8c89e1]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b6139016-94f4-460d-a4e7-8a4004e73f24
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=812, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 666c5190-3e16-47d8-9f59-aacea6ab4331
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5a5fd855-2040-498e-bd25-370707ec7232]
name                : eth23

_uuid               : 780a2a2c-55a3-4aae-9466-d5df232e95e6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [00ed8489-5616-4d83-af58-c933d9ece401]
name                : eth21

_uuid               : dc05fe81-b6c6-47fb-a33e-1e5c135546b1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8d9efdcb-3ac3-4e51-bf3a-50596fe86c85]
name                : br0

_uuid               : e9a733b7-e855-41fd-ad21-13aeec8c89e1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b0364fc1-94a4-4668-b513-67031133e477]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b0364fc1-94a4-4668-b513-67031133e477
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=738637788, tx_dropped=0, tx_errors=0, tx_packets=49177626}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 5a5fd855-2040-498e-bd25-370707ec7232
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1505524500, tx_dropped=0, tx_errors=0, tx_packets=1003683}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 00ed8489-5616-4d83-af58-c933d9ece401
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
statistics          : {collisions=0, rx_bytes=671621707, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=83504676, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8d9efdcb-3ac3-4e51-bf3a-50596fe86c85
admin_state         : down
ifindex             : 53
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
