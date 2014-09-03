---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d4e21094-ff1a-4794-aee3-dc021bfaa4f8
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
_uuid               : a0eefa06-d5ff-4788-9fda-2e44d6165792
controller          : [694acd76-0fb0-409c-b641-59c6903b3b52]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [533489de-c0ec-4d25-bd77-b9aa096e50dd, 6fe0bbd8-0054-4efd-bc39-504b75df8a15, e24c8680-fa57-4ac0-807e-88b46497cebd, f8f29b87-3fae-4f2e-9817-aa84c31bf31a]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 694acd76-0fb0-409c-b641-59c6903b3b52
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=676, sec_since_disconnect=7, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6fe0bbd8-0054-4efd-bc39-504b75df8a15
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a46dbad7-aec2-4f29-9be5-b327828c73fd]
name                : eth21

_uuid               : e24c8680-fa57-4ac0-807e-88b46497cebd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4849e78b-8515-47c9-a682-795c7eb2125f]
name                : br0

_uuid               : 533489de-c0ec-4d25-bd77-b9aa096e50dd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bc0b4c50-7137-4472-9963-43c40bd2debc]
name                : eth23

_uuid               : f8f29b87-3fae-4f2e-9817-aa84c31bf31a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [04084795-1ef6-400e-a549-de69eb9e1ee0]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : bc0b4c50-7137-4472-9963-43c40bd2debc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3256564500, tx_dropped=0, tx_errors=0, tx_packets=2171043}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 04084795-1ef6-400e-a549-de69eb9e1ee0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1216038760, tx_dropped=0, tx_errors=0, tx_packets=23727762}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 4849e78b-8515-47c9-a682-795c7eb2125f
admin_state         : down
duplex              : full
ifindex             : 90
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

_uuid               : a46dbad7-aec2-4f29-9be5-b327828c73fd
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
statistics          : {collisions=0, rx_bytes=2742878154, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=33348444, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a1fdee136b278e575d84aeeac06374a44a530300
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Thu Aug 21 15:54:07 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Wed Sep 3 13:29:03 2014 -0700

    dpif-netdev: Introduce port_try_ref&#40;&#41; to prevent a race.
    
    When pmd thread interates through all ports for queue loading,
    the main thread may unreference and 'rcu-free' a port before
    pmd thread take new reference of it.  This could cause pmd
    thread fail the reference and access freed memory later.
    
    This commit fixes this race by introducing port_try_ref&#40;&#41;
    which uses ovs_refcount_try_ref_rcu&#40;&#41;.  And the pmd thread
    will only load the port's queue, if port_try_ref&#40;&#41; returns
    true.
    
    Found by inspection.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
