---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b6cadb88-e642-4d35-b692-ad3e4ee37078
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d153d2c0-4655-4901-9b14-2fc582c17533
controller          : [e95a84a4-c6d8-4974-afae-7a90253844fe]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [498cd42d-81ac-484b-88a4-ca832c0cf63f, 5552c23a-63d8-4f79-96c0-b09d7a00b0d1, 7dcd7c0d-a3c0-49ef-b044-7f3cc100fc98, 9015602b-3301-4d8b-b6ac-ea778ba16957]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e95a84a4-c6d8-4974-afae-7a90253844fe
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7dcd7c0d-a3c0-49ef-b044-7f3cc100fc98
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [66b8dd52-d3e6-417c-a0c7-f174ce22ff7a]
name                : "eth23"

_uuid               : 498cd42d-81ac-484b-88a4-ca832c0cf63f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [274204ae-31e8-489b-a308-14abd5eac96f]
name                : "eth21"

_uuid               : 5552c23a-63d8-4f79-96c0-b09d7a00b0d1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [43dbba73-310a-4c59-b2e7-9809233dc73f]
name                : "eth22"

_uuid               : 9015602b-3301-4d8b-b6ac-ea778ba16957
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0da98571-6bee-4259-b360-0336f7f8dc78]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0da98571-6bee-4259-b360-0336f7f8dc78
admin_state         : down
duplex              : full
ifindex             : 163
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

_uuid               : 66b8dd52-d3e6-417c-a0c7-f174ce22ff7a
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

_uuid               : 274204ae-31e8-489b-a308-14abd5eac96f
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

_uuid               : 43dbba73-310a-4c59-b2e7-9809233dc73f
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 69f8f7e1388486e098ef95dba650345a91361cd1
Author:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
AuthorDate: Tue Jun 16 16:25:24 2015 +0100
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Tue Jun 16 08:37:14 2015 -0700

    ovs-vtep: Support userspace datapaths.
    
    With this commit, the VTEP emulator detects the datapath_type of the
    bridge used as a &quot;physical&quot; switch, and creates subsequent bridges
    with the same type.  This allows ovs-vtep to work with the userspace
    datapath.
    
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    Acked-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
