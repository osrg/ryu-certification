---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
06cccd2a-954a-43e1-83c6-1ec0854392e3
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : bb0d4f58-221c-4944-89e6-a8e63212947f
controller          : [60497e3d-79ff-4c82-8a7a-60c4d2427b01]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [b6e56325-30bb-40ec-acb0-a76007329382, e087dc9e-0ecf-424e-b517-a1b7fe8ed5a8, e0ac1cb8-4720-420f-b17b-3c9e42369357, f6255c6b-3aa0-480e-bd20-b208c19e7e39]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 60497e3d-79ff-4c82-8a7a-60c4d2427b01
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=967, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e0ac1cb8-4720-420f-b17b-3c9e42369357
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c2133a48-2b9b-4ecf-93d5-0c14af9ca911]
name                : br0

_uuid               : b6e56325-30bb-40ec-acb0-a76007329382
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [08395f4e-c8f1-43a6-9e84-eb640bf0b3d3]
name                : eth21

_uuid               : e087dc9e-0ecf-424e-b517-a1b7fe8ed5a8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [63b4b97e-0d45-4bcf-81b7-85a56062857c]
name                : eth22

_uuid               : f6255c6b-3aa0-480e-bd20-b208c19e7e39
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8707840e-f498-4b1a-9a60-a7b9caf2867a]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c2133a48-2b9b-4ecf-93d5-0c14af9ca911
admin_state         : down
duplex              : full
ifindex             : 360
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

_uuid               : 08395f4e-c8f1-43a6-9e84-eb640bf0b3d3
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
statistics          : {collisions=0, rx_bytes=3632829784, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=11061132, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8707840e-f498-4b1a-9a60-a7b9caf2867a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3995984204, tx_dropped=0, tx_errors=0, tx_packets=5527301}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 63b4b97e-0d45-4bcf-81b7-85a56062857c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2803136994, tx_dropped=0, tx_errors=0, tx_packets=4749656}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 50a1a1d2cc2b8fb573076ff6ee0e4f790919118b
Author:     Ryan Wilson &lt;wryan@nicira.com&gt;
AuthorDate: Mon Jun 2 22:47:15 2014 -0700
Commit:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
CommitDate: Thu Jun 5 02:34:56 2014 +0900

    timeval: Add monotonic time functionality for NetBSD and FreeBSD.
    
    This patch also checks the system platform as clock_gettime
    could exist on different platforms but with different values of
    CLOCK_MONOTONIC and different definitions of 'struct timespec'.
    In this case, the system call would be expected to catch the
    error, which is dangerous.
    
    This patch ensures Linux, NetBSD and FreeBSD platforms use
    clock_gettime with their corresponding correct values and
    definitions. All other platforms use time.time&#40;&#41;.
    
    Signed-off-by: Ryan Wilson &lt;wryan@nicira.com&gt;
    Acked-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
</pre>
