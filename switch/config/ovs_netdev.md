---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4971fe61-db48-413f-811b-292e5bab47a2
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f22dd035-8c8c-4a47-8711-197be86471b6
controller          : [bcb1554e-1f33-4e46-9125-ac0c8fe38bc9]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [17a66460-e850-4931-8f54-ee743b5e57de, 72eb0733-9aeb-4faa-850c-f548916f2cb4, 9ba0084c-c8cd-4735-b739-623cbb25142a, dfc21e5e-36ab-407e-b52e-abced1d96a8a]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : bcb1554e-1f33-4e46-9125-ac0c8fe38bc9
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 17a66460-e850-4931-8f54-ee743b5e57de
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d2f5cda4-ac88-4053-b7a4-e3c4c14d7620]
name                : "eth23"

_uuid               : 9ba0084c-c8cd-4735-b739-623cbb25142a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6246282e-43f4-4e90-86d0-8561b8ed4065]
name                : "eth21"

_uuid               : dfc21e5e-36ab-407e-b52e-abced1d96a8a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ce00b538-cd40-4be3-8cfa-36e2e5bfff49]
name                : "eth22"

_uuid               : 72eb0733-9aeb-4faa-850c-f548916f2cb4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [33573506-b0f7-450c-ba7b-5d4189581144]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d2f5cda4-ac88-4053-b7a4-e3c4c14d7620
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1176922500, tx_dropped=0, tx_errors=0, tx_packets=784615}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ce00b538-cd40-4be3-8cfa-36e2e5bfff49
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18089315792, tx_dropped=0, tx_errors=0, tx_packets=12064077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 33573506-b0f7-450c-ba7b-5d4189581144
admin_state         : down
duplex              : full
ifindex             : 463
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

_uuid               : 6246282e-43f4-4e90-86d0-8561b8ed4065
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
statistics          : {collisions=0, rx_bytes=24024581534, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16026376, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 88058f19ed9aadb1b22d26d93e46b3fd5eb1ad32
Author:     Alex Wang &lt;ee07b291@gmail.com&gt;
AuthorDate: Fri Aug 7 00:21:42 2015 -0700
Commit:     Alex Wang &lt;ee07b291@gmail.com&gt;
CommitDate: Tue Sep 15 07:20:10 2015 +0000

    ovn-controller-vtep: Update related documentation.
    
    This commit conducts the following documentation changes:
    
    *   add a description in ovn-architecture manual for
        the life cycle about VTEP gateway.
    
    *   add TODOs related to ovn-controller-vtep.
    
    *   refine the ovn-sb, ovn-nb schema manual to require
        logical 'port' type and 'options' configuration.
    
    Signed-off-by: Alex Wang &lt;ee07b291@gmail.com&gt;
    Acked-by: Russell Bryant &lt;rbryant@redhat.com&gt;
    Acked-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
