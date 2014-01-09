---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
276bd710-ac55-4afe-b05d-50d8e5f7f2e3
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth7"
            Interface "eth7"
        Port "eth8"
            Interface "eth8"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge
_uuid               : ca54d4fa-83d4-4662-9d75-565d76cbd251
controller          : [1db85aff-5ca1-421d-83b9-d8af3d48dc60]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0f24bce8-919b-41d9-a334-d26524ddd85b, 39dc905b-5e7a-4fa9-b57e-80afad005118, e20d2a98-33d1-4f8a-ba6c-d6c99f783773]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 1db85aff-5ca1-421d-83b9-d8af3d48dc60
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="297", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : e20d2a98-33d1-4f8a-ba6c-d6c99f783773
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [14dfc203-c9c8-4e9c-9bbe-e2a058f666a9]
name                : "br0"

_uuid               : 0f24bce8-919b-41d9-a334-d26524ddd85b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dfb1d6d3-8e61-407b-94dc-cc16b79d5901]
name                : "eth7"

_uuid               : 39dc905b-5e7a-4fa9-b57e-80afad005118
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d6f0d22c-a7ce-418b-9728-cb6fffd60ec3]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : d6f0d22c-a7ce-418b-9728-cb6fffd60ec3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1034456, tx_dropped=0, tx_errors=0, tx_packets=11154}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : dfb1d6d3-8e61-407b-94dc-cc16b79d5901
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
statistics          : {collisions=0, rx_bytes=3117041, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31642, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 14dfc203-c9c8-4e9c-9bbe-e2a058f666a9
admin_state         : up
duplex              : full
ifindex             : 133
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
