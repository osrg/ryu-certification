---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a4f16795-7661-4c73-8136-9c3d8657221e
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
_uuid               : 5d64f37c-1bbb-421a-82e7-fd3be312aa05
controller          : [5b4d9f63-39e2-4fbe-ba30-4a3b98a3235d]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1e9d3bcc-bf92-4e1f-ac4f-21b25152446a, 90b8496c-8562-4014-8f71-2a23476c6e8c, a0387256-eb1c-4b5b-aede-37712cf9b746, b6f04d8a-168c-42a9-8946-efc87c78dd6e]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5b4d9f63-39e2-4fbe-ba30-4a3b98a3235d
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1e9d3bcc-bf92-4e1f-ac4f-21b25152446a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e25e399b-602f-48df-a865-f83e1b7be10a]
name                : "eth21"

_uuid               : 90b8496c-8562-4014-8f71-2a23476c6e8c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [24bbb7a6-fc05-4732-aece-183f8705b710]
name                : "eth22"

_uuid               : b6f04d8a-168c-42a9-8946-efc87c78dd6e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f3bd9414-7975-4aa3-8b5a-b2c484465c10]
name                : "eth23"

_uuid               : a0387256-eb1c-4b5b-aede-37712cf9b746
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b1273f2b-10bd-4711-87df-1d57db035a52]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f3bd9414-7975-4aa3-8b5a-b2c484465c10
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

_uuid               : 24bbb7a6-fc05-4732-aece-183f8705b710
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

_uuid               : b1273f2b-10bd-4711-87df-1d57db035a52
admin_state         : down
duplex              : full
ifindex             : 106
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

_uuid               : e25e399b-602f-48df-a865-f83e1b7be10a
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3bcc10c0701c241ef62bdb32c5d21c060ad7590b
Author:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
AuthorDate: Wed Jun 3 15:55:16 2015 +0100
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Wed Jun 3 15:34:58 2015 -0700

    dpif-netdev: Fix non-pmd thread queue id.
    
    Non pmd threads have a core_id == UINT32_MAX, while queue ids used by
    netdevs range from 0 to the number of CPUs.  Therefore core ids cannot
    be used directly to select a queue.
    
    This commit introduces a simple mapping to fix the problem: pmd threads
    continue using queues 0 to N &#40;where N is the number of CPUs in the
    system&#41;, while non pmd threads use queue N+1.
    
    Fixes: d5c199ea7ff7 &#40;&quot;netdev-dpdk: Properly support non pmd threads.&quot;&#41;
    
    Reported-by: 차은호 &lt;eunho.cha@atto-research.com
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    Signed-off-by: Mark D. Gray &lt;mark.d.gray@intel.com&gt;
    Signed-off-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Acked-by: Flavio Leitner &lt;fbl@redhat.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
