---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4050a345-fbd4-437e-a808-06f864791dec
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : da852ee1-f0d3-49ad-9f21-d2a1dea1660c
controller          : [99f8a612-9dd2-46f7-a056-3205710c107b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [07d6d334-0780-409e-a11e-6d83fc6c7ee9, 46517d99-b737-4c0c-8ff2-641e0704b2e2, 825f0fd0-b6da-400b-8499-e95fba3e10a6, f6fc4e0c-0ef0-4a02-b99f-6588ebe07559]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 99f8a612-9dd2-46f7-a056-3205710c107b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="767", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 07d6d334-0780-409e-a11e-6d83fc6c7ee9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b72a05c7-0d84-4f36-939f-29b1b87629fb]
name                : "br0"

_uuid               : 825f0fd0-b6da-400b-8499-e95fba3e10a6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [616c30e0-b21f-420a-a2be-bd96dbed5cd4]
name                : "eth23"

_uuid               : f6fc4e0c-0ef0-4a02-b99f-6588ebe07559
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9a2df87d-474d-437b-9739-aa2325e4a60d]
name                : "eth21"

_uuid               : 46517d99-b737-4c0c-8ff2-641e0704b2e2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8e9c22a4-5f13-43c0-a479-16ec2d29cc01]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 616c30e0-b21f-420a-a2be-bd96dbed5cd4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4322053500, tx_dropped=0, tx_errors=0, tx_packets=2881369}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 8e9c22a4-5f13-43c0-a479-16ec2d29cc01
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=27928652968, tx_dropped=0, tx_errors=0, tx_packets=18633936}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9a2df87d-474d-437b-9739-aa2325e4a60d
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
statistics          : {collisions=0, rx_bytes=39482192484, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26355135, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b72a05c7-0d84-4f36-939f-29b1b87629fb
admin_state         : down
duplex              : full
ifindex             : 595
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 2979b9158bff4d6fcbddf7e09131a8cfeb9ec746
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Thu Oct 22 10:29:56 2015 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Thu Oct 22 19:53:45 2015 -0700

    bfd: always export remote_state and remote_diagnostic to OVSDB
    
    RFC 5880 specified bfd.RemoteSessionState as one of the state
    variables.  In OVS implementation, this value is exported to OVSDB's
    BFD status column of the interface table, as one of the map elements,
    with the key of 'remote_state'.
    
    It can be surprising when the 'remote_state' map element disappears
    when BFD is in the 'DOWN' state, but otherwise always exported.
    Change to always exporting it, to make it more predictable for
    applications that monitors the BFD status column.
    
    While at it, make the same change to 'remote_diagnostic', so that it
    is also always exported to OVSDB for consistency.
    
    VMWare-BZ: 1535979
    Reported-by: Mihir Gangar &lt;gangarm@vmware.com&gt;
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
