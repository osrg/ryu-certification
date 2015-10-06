---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3d3907de-b1d9-42a3-b9d3-e8a8d4f7ad79
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e0e709aa-ac73-4ae6-b68a-a83a4313b917
controller          : [a88bea61-06a0-4853-9cdc-7bbce69e5bcf]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0d2d343e-063c-4385-ab04-ec9cba8e5870, a3f51dfa-3c76-4a45-a97b-eccfdeb8547c, aa4bffb7-f908-41ec-84b6-02ffaaaf2767, f3e27417-7025-4a7e-933e-f235af46e777]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a88bea61-06a0-4853-9cdc-7bbce69e5bcf
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="757", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0d2d343e-063c-4385-ab04-ec9cba8e5870
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ed6dced8-3065-48d2-aa51-92114ec5253d]
name                : "eth23"

_uuid               : a3f51dfa-3c76-4a45-a97b-eccfdeb8547c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5d1e5d65-dce3-4f38-bb10-a50f4ee3e29a]
name                : "eth22"

_uuid               : aa4bffb7-f908-41ec-84b6-02ffaaaf2767
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a07d0c6f-4ca1-4fb3-b160-bc5f6cef26b3]
name                : "br0"

_uuid               : f3e27417-7025-4a7e-933e-f235af46e777
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a156864d-bd01-46b2-8e90-b6e63b7616cc]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ed6dced8-3065-48d2-aa51-92114ec5253d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1735014000, tx_dropped=0, tx_errors=0, tx_packets=1156676}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 5d1e5d65-dce3-4f38-bb10-a50f4ee3e29a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=26318573836, tx_dropped=0, tx_errors=0, tx_packets=17552348}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a156864d-bd01-46b2-8e90-b6e63b7616cc
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
statistics          : {collisions=0, rx_bytes=35983475291, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=24003583, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a07d0c6f-4ca1-4fb3-b160-bc5f6cef26b3
admin_state         : down
duplex              : full
ifindex             : 536
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
