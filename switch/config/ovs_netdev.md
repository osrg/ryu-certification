---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
136d9c87-96c6-4d31-9848-dbf71e7472ea
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b68d068d-e4f5-4ced-b698-be395bfa0736
controller          : [ef2bbee0-c002-411d-a840-b2e0a3fddd14]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3b7cf919-0850-41ba-9ee1-53489e12be3f, a6527e76-448a-4eb9-925d-85c4a05d4b2e, e5ec84d1-42e3-47b0-92b2-0905d361dcf5, f9255844-8e63-4ae6-9847-6deafdf551ac]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ef2bbee0-c002-411d-a840-b2e0a3fddd14
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="4", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f9255844-8e63-4ae6-9847-6deafdf551ac
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [08d83377-333a-41f8-b850-b8ada63ba190]
name                : "br0"

_uuid               : e5ec84d1-42e3-47b0-92b2-0905d361dcf5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d678321e-1e11-460b-ac85-d7b998e5485c]
name                : "eth22"

_uuid               : 3b7cf919-0850-41ba-9ee1-53489e12be3f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [90525587-625f-4061-8f7b-5ae16cb0d998]
name                : "eth23"

_uuid               : a6527e76-448a-4eb9-925d-85c4a05d4b2e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4e3550cc-9ba6-48ae-ba46-0c27b2f0c6c2]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4e3550cc-9ba6-48ae-ba46-0c27b2f0c6c2
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
statistics          : {collisions=0, rx_bytes=44853344047, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29965763, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d678321e-1e11-460b-ac85-d7b998e5485c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30382940365, tx_dropped=0, tx_errors=0, tx_packets=20284246}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 90525587-625f-4061-8f7b-5ae16cb0d998
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=8311090500, tx_dropped=0, tx_errors=0, tx_packets=5540727}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 08d83377-333a-41f8-b850-b8ada63ba190
admin_state         : down
duplex              : full
ifindex             : 760
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
commit 88779d665a5aa2141c7efdb3d5902435f051e949
Author:     Russell Bryant &lt;russell@ovn.org&gt;
AuthorDate: Wed Feb 3 11:46:33 2016 -0500
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Wed Feb 3 11:49:40 2016 -0500

    ovn: Update comment about local datapath calculation.
    
    ovn-controller has a simple optimization for excluding some logical flow
    processing that we know is unnecessary.  This update to a comment in the
    code reflects a discussion we had on the mailing list about a better
    algorithm that would let us exclude even more.
    
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
</pre>
