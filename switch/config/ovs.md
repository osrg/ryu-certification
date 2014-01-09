---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0476892f-ebb5-4966-8ec7-825df18a1909
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth8"
            Interface "eth8"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth7"
            Interface "eth7"

$ sudo ovs-vsctl list Bridge
_uuid               : cd1ed86f-b1df-4850-a8ad-884e958430ce
controller          : [b9cdc973-d4f4-4d1c-b41e-6f395cdc2fbb]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [34540ca7-655c-4821-ba1f-2e4bdbd18907, 4c32f2a5-2ed6-45ec-aa94-bb9d0068b954, dc86931a-542c-42b9-a884-3a1b5d2c09dc]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : b9cdc973-d4f4-4d1c-b41e-6f395cdc2fbb
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="352", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 4c32f2a5-2ed6-45ec-aa94-bb9d0068b954
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [250298fa-807c-4bba-97b4-69bd6595704b]
name                : "br0"

_uuid               : dc86931a-542c-42b9-a884-3a1b5d2c09dc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4aad68e7-13c7-4f84-b913-af633ff9571b]
name                : "eth7"

_uuid               : 34540ca7-655c-4821-ba1f-2e4bdbd18907
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [20b26f8e-fa9a-4255-bfe1-7295871ba8c1]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : 250298fa-807c-4bba-97b4-69bd6595704b
admin_state         : up
ifindex             : 141
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 20b26f8e-fa9a-4255-bfe1-7295871ba8c1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 4aad68e7-13c7-4f84-b913-af633ff9571b
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
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
