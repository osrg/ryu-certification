---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
61609cfc-98d5-479e-9169-2cc0c39aad98
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 84add920-eaec-4fbd-8a87-84dbda9f5bbd
controller          : [33aa281b-dee0-497f-a7d2-881219804129]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [165676a0-c64d-4a3e-afa1-1aff0a2b216e, e57fac9c-558d-4309-b303-c8e151cc4960, e8e47565-d7a6-4d41-8179-8a36a7b97726, fecbaba4-5021-40c3-b17f-abe0d54c24f2]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 33aa281b-dee0-497f-a7d2-881219804129
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=966, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : fecbaba4-5021-40c3-b17f-abe0d54c24f2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [380b62b4-eb0f-4381-a4e0-ac8b1a3bbe99]
name                : eth22

_uuid               : 165676a0-c64d-4a3e-afa1-1aff0a2b216e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [eb3a491b-3a98-4f7f-bc8e-74be22547228]
name                : eth21

_uuid               : e57fac9c-558d-4309-b303-c8e151cc4960
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [98b32a8b-841f-463e-b61b-ece50c20c8bc]
name                : eth23

_uuid               : e8e47565-d7a6-4d41-8179-8a36a7b97726
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [612ab563-f1c1-43fe-ac18-6c7d090fae65]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 380b62b4-eb0f-4381-a4e0-ac8b1a3bbe99
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2540813258, tx_dropped=0, tx_errors=0, tx_packets=13177230}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 612ab563-f1c1-43fe-ac18-6c7d090fae65
admin_state         : down
duplex              : full
ifindex             : 503
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

_uuid               : 98b32a8b-841f-463e-b61b-ece50c20c8bc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3617837908, tx_dropped=0, tx_errors=0, tx_packets=8138515}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : eb3a491b-3a98-4f7f-bc8e-74be22547228
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
statistics          : {collisions=0, rx_bytes=3366154963, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28094748, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a5d4fadd0027b25cd393ba8535594227aa09b86a
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Tue May 27 21:59:26 2014 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Fri Jun 13 16:28:22 2014 -0700

    netdev-vport: Use dpif_port as base for tunnel backing port.
    
    In most cases, tunnel ports specify a dpif name to act as the backing
    port in the datapath. However, in the case of UDP tunnels the type is
    used with the port number appended. This is potentially a problem for
    IPsec tunnels because they have different types but should have the
    same backing port. The hasn't been a problem in practice though because
    no UDP tunnels are currently used with IPsec.
    
    This switches to use the dpif_port in all cases plus a port number if
    necessary. It does this by making the names short enough to accomodate
    ports, which also makes the naming more consistent.
    
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
