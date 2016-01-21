---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
40c6f841-740b-4a3d-9b73-7050e945fbda
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 40391722-702a-4b3f-94e3-03de5f5d1654
controller          : [e8e3cc6d-a357-46b4-89b4-a2fe0bf4ad94]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [5ac975bd-7e45-4b9a-a3bb-24d0dd7d7241, 5e1011fe-f8ee-4572-9a51-354a6d4da496, 64406471-c0f0-4478-9b46-0c6163ad2141, 7bcbc9dd-34e3-4b6a-830a-4a8a5fde1105]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e8e3cc6d-a357-46b4-89b4-a2fe0bf4ad94
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 64406471-c0f0-4478-9b46-0c6163ad2141
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [41374281-ef86-4a8e-a1d6-6ec5dacf9950]
name                : "eth22"

_uuid               : 5ac975bd-7e45-4b9a-a3bb-24d0dd7d7241
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [176824b1-a3d4-480f-a947-231f19fca5ba]
name                : "eth21"

_uuid               : 7bcbc9dd-34e3-4b6a-830a-4a8a5fde1105
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [02ef4d1e-b23a-4dda-b49e-cfbdbc5c3ac9]
name                : "eth23"

_uuid               : 5e1011fe-f8ee-4572-9a51-354a6d4da496
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5995ee19-2af4-48f0-8d81-75585f070ebe]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 5995ee19-2af4-48f0-8d81-75585f070ebe
admin_state         : down
duplex              : full
ifindex             : 720
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

_uuid               : 41374281-ef86-4a8e-a1d6-6ec5dacf9950
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29856336035, tx_dropped=0, tx_errors=0, tx_packets=19929969}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 176824b1-a3d4-480f-a947-231f19fca5ba
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
statistics          : {collisions=0, rx_bytes=43683151137, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29179057, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 02ef4d1e-b23a-4dda-b49e-cfbdbc5c3ac9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7433925000, tx_dropped=0, tx_errors=0, tx_packets=4955950}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 8d24e9c06b15399259c0324fc6c5c83174291014
Author:     Russell Bryant &lt;russell@ovn.org&gt;
AuthorDate: Wed Jan 20 11:17:58 2016 -0500
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Thu Jan 21 11:50:01 2016 -0500

    ovn-controller: Update check for parent port.
    
    There were a couple of checks that checked for a parent port as the
    field being non-NULL.  We should treat an empty string the same as NULL
    for this field.
    
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
