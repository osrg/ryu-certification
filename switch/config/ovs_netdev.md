---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
473343bb-bbac-4101-94c2-7bc46196bb00
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth8"
            Interface "eth8"
        Port "eth7"
            Interface "eth7"

$ sudo ovs-vsctl list Bridge
_uuid               : f9c2839d-ef4a-4579-8a0d-5707ff099dee
controller          : [66f43f47-05fe-48e5-89c6-6722917391f7]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [335882ec-2d10-4136-88f8-fe554af45d93, 9beadb70-3658-4138-ab7e-b4cc181adf86, f18f8667-a913-4b9e-8540-a8540f1ff105]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 66f43f47-05fe-48e5-89c6-6722917391f7
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="296", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 335882ec-2d10-4136-88f8-fe554af45d93
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4063a330-7433-4e80-a818-7eeda5c21339]
name                : "br0"

_uuid               : 9beadb70-3658-4138-ab7e-b4cc181adf86
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [475d146c-b1e9-462e-a024-b27739e28f32]
name                : "eth8"

_uuid               : f18f8667-a913-4b9e-8540-a8540f1ff105
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4d26118d-100a-4671-bac2-678da5a32606]
name                : "eth7"

$ sudo ovs-vsctl list Interface
_uuid               : 475d146c-b1e9-462e-a024-b27739e28f32
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:ec"
mtu                 : 1550
name                : "eth8"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=973076, tx_dropped=0, tx_errors=0, tx_packets=10494}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 4063a330-7433-4e80-a818-7eeda5c21339
admin_state         : up
duplex              : full
ifindex             : 127
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : 4d26118d-100a-4671-bac2-678da5a32606
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "eth7"
ofport              : 1
statistics          : {collisions=0, rx_bytes=2921246, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29662, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 615309cfb6992867251d01f1c34955568b3950ea
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Wed Jan 8 18:51:43 2014 -0800
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Wed Jan 8 18:57:04 2014 -0800

    bfd: Fix cpath_down set failure.
    
    Commit ccc09689 (bfd: Implement Bidirectional Forwarding Detection.)
    set the bfd local diagnostic to "Concatenated Path Down" in response
    to the set of cpath_down only when the current local diagnostic is
    "None".  However, since the bfd local diagnostic is not reset when
    the bfd state is restored from last erroneous state, the set of
    cpath_down will not update the local diagnostic in that case.
    
    This commit fixes the bug by always checking for local diagnostic
    change when cpath_down is set or reset.
    
    Bug #22625
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Signed-off-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
