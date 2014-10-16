---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ce73829b-8543-4b94-9c66-5addacb9d511
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0d9b824b-290c-48e1-966c-4295e5676059
controller          : [afd494a2-21db-4b3f-a2af-93bd188ee12f]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0445ed86-93a5-4ee6-a671-9a813a9fee91, 12cc733f-18d6-41ad-89e4-d41287251628, a8c5544d-4ab4-4f9d-865a-75894ebe200e, d266e9a1-3018-406e-9d48-5663e3a49866]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : afd494a2-21db-4b3f-a2af-93bd188ee12f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=667, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a8c5544d-4ab4-4f9d-865a-75894ebe200e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2034d1e5-b29f-41c4-9fec-873cbd420fa3]
name                : eth23

_uuid               : d266e9a1-3018-406e-9d48-5663e3a49866
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [296e550e-ba97-417f-a3ea-18c729657658]
name                : br0

_uuid               : 0445ed86-93a5-4ee6-a671-9a813a9fee91
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b1a392b3-03ed-42bd-83bc-48eb64d45ced]
name                : eth21

_uuid               : 12cc733f-18d6-41ad-89e4-d41287251628
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a09eccb8-7ab9-4e1c-b32c-2bf6c5c06b60]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a09eccb8-7ab9-4e1c-b32c-2bf6c5c06b60
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1877253470, tx_dropped=0, tx_errors=0, tx_packets=104369944}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2034d1e5-b29f-41c4-9fec-873cbd420fa3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2623859908, tx_dropped=0, tx_errors=0, tx_packets=7475863}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 296e550e-ba97-417f-a3ea-18c729657658
admin_state         : down
duplex              : full
ifindex             : 254
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

_uuid               : b1a392b3-03ed-42bd-83bc-48eb64d45ced
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
statistics          : {collisions=0, rx_bytes=977032801, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=169674033, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 10ab94fef2fc44902c1b16e06e4f4edcc3da7583
Author:     Niels van Adrichem &lt;N.L.M.vanAdrichem@tudelft.nl&gt;
AuthorDate: Wed Oct 15 13:54:52 2014 +0000
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Oct 16 09:30:40 2014 -0700

    ofproto-dpif-xlate: Use bfd forwarding status in fast-failover groups.
    
    Integration of each interface' status as confirmed by BFD into the
    FastFailover Group table. When BFD is configured and function
    bfd_forwarding&#40;&#41; reports false, odp_port_is_alive also reports false in
    order to have a watched interface report false and omit to another
    backup.
    
    Test-suite has been succesfully run, as well as testing with ICMP echo
    requests and replies that traffic was succesfully rerouted over the
    backup path. More extensive load-consumption tests with a function that
    only checked whether &#40;bfd-&gt;state == STATE_UP&#41; have been succesfully
    performed, but was later changed to use the larger function
    bfd_forwarding&#40;&#41; as it captures all possible exceptions and is properly
    mutually excluded.
    
    Signed-off-by: Niels van Adrichem &lt;n.l.m.vanadrichem@tudelft.nl&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
