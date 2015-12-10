---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f7eae343-e0cd-4cab-8c23-3233e1772607
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : deb207d2-1119-43aa-b1b8-89df9ec20900
controller          : [2c2695f7-4add-489f-9aa0-5fc7ca4efd7d]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [433bf912-6689-49f1-9745-0411a5b09bac, 466ea172-a971-4a98-9491-500ce6fd125a, 5228d38a-8758-416e-b50a-e3ac908cfdf2, e964b0ea-48ac-4f0b-9339-d8c48279db7b]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2c2695f7-4add-489f-9aa0-5fc7ca4efd7d
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5228d38a-8758-416e-b50a-e3ac908cfdf2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [182a73d2-ee42-49d2-82e5-d7dbb083c70f]
name                : "br0"

_uuid               : 433bf912-6689-49f1-9745-0411a5b09bac
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d7568c59-0ff8-47dc-8ffd-7431621f08f4]
name                : "eth21"

_uuid               : 466ea172-a971-4a98-9491-500ce6fd125a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0b7d2e92-db64-4edf-82a6-5d9fdafc45d7]
name                : "eth22"

_uuid               : e964b0ea-48ac-4f0b-9339-d8c48279db7b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [96f0c0d8-1ade-4438-98e4-61aa63defe70]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 96f0c0d8-1ade-4438-98e4-61aa63defe70
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6205848000, tx_dropped=0, tx_errors=0, tx_packets=4137232}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d7568c59-0ff8-47dc-8ffd-7431621f08f4
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
statistics          : {collisions=0, rx_bytes=42044886679, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28077678, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 182a73d2-ee42-49d2-82e5-d7dbb083c70f
admin_state         : down
duplex              : full
ifindex             : 668
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

_uuid               : 0b7d2e92-db64-4edf-82a6-5d9fdafc45d7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29119124689, tx_dropped=0, tx_errors=0, tx_packets=19434010}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5a6b18a979ddda3f9cd8ff774397a9ad02bdc20f
Author:     Russell Bryant &lt;russell@ovn.org&gt;
AuthorDate: Wed Dec 9 14:04:01 2015 -0500
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Wed Dec 9 16:27:05 2015 -0500

    CONTRIBUTING: Document the Fixes header.
    
    Document the use of the Fixes header to refer to a commit that
    introduced a bug being fixed.
    
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
    Acked-by: Joe Stringer &lt;joe@ovn.org&gt;
</pre>
