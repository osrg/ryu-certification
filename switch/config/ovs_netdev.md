---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6a8292be-f529-4b25-830e-c0e4c7b4c8f3
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth7"
            Interface "eth7"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth8"
            Interface "eth8"

$ sudo ovs-vsctl list Bridge
_uuid               : 44436554-eacc-4b8d-b427-8ad045d4443c
controller          : [b8deaba4-4ae0-43be-bef3-9364d62e282c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [6f4f96f2-72c1-486c-afb2-0d42f7c16d70, 8f6662a7-f1dc-4d23-913d-4715bca168f4, eb73d3bf-a691-405a-8ec7-6c03252ab6a2]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : b8deaba4-4ae0-43be-bef3-9364d62e282c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="297", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 6f4f96f2-72c1-486c-afb2-0d42f7c16d70
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d79c661e-bc17-4a14-bb20-eb77f2bb4b91]
name                : "eth7"

_uuid               : 8f6662a7-f1dc-4d23-913d-4715bca168f4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [433116b8-fee4-484e-83f9-99b6a4c7e925]
name                : "br0"

_uuid               : eb73d3bf-a691-405a-8ec7-6c03252ab6a2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [46d34bdc-75a8-469f-8949-cbb4ae75a4a8]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : 46d34bdc-75a8-469f-8949-cbb4ae75a4a8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1095608, tx_dropped=0, tx_errors=0, tx_packets=11814}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 433116b8-fee4-484e-83f9-99b6a4c7e925
admin_state         : up
duplex              : full
ifindex             : 139
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

_uuid               : d79c661e-bc17-4a14-bb20-eb77f2bb4b91
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
statistics          : {collisions=0, rx_bytes=3312836, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=33622, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
