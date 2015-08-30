---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8803dd3e-3310-48a1-9519-7496d6a0ffb8
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 205ad503-f051-498e-85ef-9bff14fe8ceb
controller          : [a5b69918-a4e5-4a81-b6c4-76364aea0068]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [09bdab53-6f17-40fb-8312-3ab24a2664e1, 7ec1eec0-38ee-402d-a2d4-0226e32835ec, 933d69b0-9eb4-4bd3-9caa-fc3dec322bf7, ee660c73-78d8-463f-afc9-0b8c80760d13]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a5b69918-a4e5-4a81-b6c4-76364aea0068
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 933d69b0-9eb4-4bd3-9caa-fc3dec322bf7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [48f3171c-b32c-43ab-bb40-99ca8b3168b1]
name                : "eth22"

_uuid               : 7ec1eec0-38ee-402d-a2d4-0226e32835ec
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5b2847aa-49a8-47f9-931a-aab0c75003f1]
name                : "eth21"

_uuid               : 09bdab53-6f17-40fb-8312-3ab24a2664e1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9532e70b-6818-40e4-add6-2d2c36277c56]
name                : "br0"

_uuid               : ee660c73-78d8-463f-afc9-0b8c80760d13
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ce1e801b-9aed-49f3-8164-2e0720f1f40b]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 48f3171c-b32c-43ab-bb40-99ca8b3168b1
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

_uuid               : 5b2847aa-49a8-47f9-931a-aab0c75003f1
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

_uuid               : 9532e70b-6818-40e4-add6-2d2c36277c56
admin_state         : down
duplex              : full
ifindex             : 409
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

_uuid               : ce1e801b-9aed-49f3-8164-2e0720f1f40b
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1cb20095c3c933aca1e7607ad2dd6ed9933b359e
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Tue Aug 11 18:41:37 2015 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Fri Aug 28 18:02:00 2015 -0700

    tunnel: Support matching on the presence of Geneve options.
    
    Sometimes it is useful to match only on whether a Geneve option
    is present even if the specific value is unimportant. A special
    case of this is zero length options where there is no value at all
    and the only information conveyed is whether the option was included
    in the packet.
    
    This operation was partially supported before but it was not consistent -
    in particular, options were never serialized through NXM/OXM unless
    they had a non-zero mask. Furthermore, zero length options were rejected
    altogether when they were installed through the Geneve map OpenFlow
    command.
    
    This adds support for these types of matches by making any NXM/OXM for
    tunnel metadata force a match on that field. In the case of a zero length
    option, both the value and mask of the NXM are ignored.
    
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
