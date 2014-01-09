---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
50576500-1814-40fb-8829-f310c1481bd6
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth8"
            Interface "eth8"
        Port "eth7"
            Interface "eth7"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge
_uuid               : 98d1ca49-b314-4892-93e7-e6a6ee1ee833
controller          : [48383a2a-c8c3-4535-937a-7981edd764a1]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0b38094b-f176-4229-a73b-2ecd552563d2, 448e585b-1bd4-4251-abae-4c580598c4bb, a776bdfd-4bf9-4462-aa68-22c1449eb836]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 48383a2a-c8c3-4535-937a-7981edd764a1
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="352", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : a776bdfd-4bf9-4462-aa68-22c1449eb836
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4f26a1c5-0cdc-4f14-af7b-aa6d5175ac88]
name                : "br0"

_uuid               : 0b38094b-f176-4229-a73b-2ecd552563d2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [09719474-e9f1-4b5b-90a2-2cd3431afb6e]
name                : "eth8"

_uuid               : 448e585b-1bd4-4251-abae-4c580598c4bb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0220d13c-6cf8-4ad4-be79-01912285ed84]
name                : "eth7"

$ sudo ovs-vsctl list Interface
_uuid               : 0220d13c-6cf8-4ad4-be79-01912285ed84
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

_uuid               : 09719474-e9f1-4b5b-90a2-2cd3431afb6e
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

_uuid               : 4f26a1c5-0cdc-4f14-af7b-aa6d5175ac88
admin_state         : up
ifindex             : 135
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
