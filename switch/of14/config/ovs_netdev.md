---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
caad1280-c29a-4bb8-90cd-2ad8d6e1c5eb
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a17e509a-8d8a-4e0e-917e-d353556c0799
controller          : [e48388dd-f23d-4b7a-92d8-013327b2fb17]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [21606572-b5a5-4c85-aa00-7cdbde9264be, 45420354-d85a-4c5f-b28e-8cbfd9751941, 86497e3d-2d48-4a45-9c02-fd8e207afdf4, 89d9e526-13cf-49b5-8327-eabb9136ba08]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e48388dd-f23d-4b7a-92d8-013327b2fb17
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="752", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 45420354-d85a-4c5f-b28e-8cbfd9751941
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5648b861-7ac4-4599-8ca9-6297282de3fb]
name                : "eth22"

_uuid               : 86497e3d-2d48-4a45-9c02-fd8e207afdf4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d0a891db-cc1c-4d1b-a9c3-61315db79f0a]
name                : "eth21"

_uuid               : 89d9e526-13cf-49b5-8327-eabb9136ba08
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [96bb7724-7636-473c-b96e-fd6db7a7cf44]
name                : "eth23"

_uuid               : 21606572-b5a5-4c85-aa00-7cdbde9264be
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9ef62f0d-a340-4153-9181-cc92c184b93d]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 96bb7724-7636-473c-b96e-fd6db7a7cf44
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1647571500, tx_dropped=0, tx_errors=0, tx_packets=1098381}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 5648b861-7ac4-4599-8ca9-6297282de3fb
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=26265652402, tx_dropped=0, tx_errors=0, tx_packets=17516792}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9ef62f0d-a340-4153-9181-cc92c184b93d
admin_state         : down
duplex              : full
ifindex             : 534
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : d0a891db-cc1c-4d1b-a9c3-61315db79f0a
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=35866468466, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=23924936, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit bb4c7107b270a941de48ae51a95978bea14fb14d
Author:     Russell Bryant &lt;rbryant@redhat.com&gt;
AuthorDate: Tue Oct 6 04:50:46 2015 +0100
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Oct 5 21:13:28 2015 -0700

    ovn-nbctl: Split parent and tag in &quot;show&quot; output.
    
    As of 779e72cc57a106251cc9e6696e8c9aabb56d30b5, localnet ports may have
    the tag column set.  This case does not make use of the parent column,
    so output these fields independently of each other.
    
    Signed-off-by: Russell Bryant &lt;rbryant@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
