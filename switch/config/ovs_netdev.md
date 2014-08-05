---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
bf690c0c-4b16-4654-8821-b54dc622322a
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 15da9a22-aa08-4137-a164-d1a51339cdde
controller          : [bdf9005f-1c3e-4afa-b654-f2aaaae4b2f0]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2551636d-c304-4041-90a2-366650684df8, 69de4b90-92f1-4d3f-91a5-db8b4e569d7a, 8e658b12-81a2-4272-be34-93c815c250e9, b1f1f9d4-3fca-4609-ac26-6a208a7a8617]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : bdf9005f-1c3e-4afa-b654-f2aaaae4b2f0
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=681, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 69de4b90-92f1-4d3f-91a5-db8b4e569d7a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [331f94a5-e568-4237-bb14-1feab8834fd6]
name                : br0

_uuid               : b1f1f9d4-3fca-4609-ac26-6a208a7a8617
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3f0d054d-4a3d-4469-ba26-7becea6663d0]
name                : eth23

_uuid               : 2551636d-c304-4041-90a2-366650684df8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3ae17113-0813-4baf-8837-b751fff770ae]
name                : eth21

_uuid               : 8e658b12-81a2-4272-be34-93c815c250e9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [26c55c1b-5087-4504-9236-8e66f6d553e7]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3f0d054d-4a3d-4469-ba26-7becea6663d0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1704048000, tx_dropped=0, tx_errors=0, tx_packets=1136032}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 331f94a5-e568-4237-bb14-1feab8834fd6
admin_state         : down
duplex              : full
ifindex             : 57
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

_uuid               : 26c55c1b-5087-4504-9236-8e66f6d553e7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=820572608, tx_dropped=0, tx_errors=0, tx_packets=49232835}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3ae17113-0813-4baf-8837-b751fff770ae
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
statistics          : {collisions=0, rx_bytes=905357123, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=83661762, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
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
