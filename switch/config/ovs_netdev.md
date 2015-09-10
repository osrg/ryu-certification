---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
605a4a67-6a6d-4718-bb16-221c3e1f3ca9
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 999b9127-5515-4a77-8efd-7a61bfc01638
controller          : [f1442d43-8b1c-48be-b466-9a2263d48f6b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [316ef777-a87b-4cad-83ab-b1e40ec1114d, 38380d7e-84a9-496e-9609-35b084468748, 6775f7d1-c8ad-436d-8dd7-20e3b5dd3939, 7544d68f-1f95-4337-ae30-fdc921daa373]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f1442d43-8b1c-48be-b466-9a2263d48f6b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6775f7d1-c8ad-436d-8dd7-20e3b5dd3939
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [721c67ee-91a7-4c83-989f-6a16ebc3071f]
name                : "eth21"

_uuid               : 38380d7e-84a9-496e-9609-35b084468748
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [684f749e-e420-48e3-aaa4-773281bd2303]
name                : "eth23"

_uuid               : 7544d68f-1f95-4337-ae30-fdc921daa373
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9509667e-158d-49c4-b245-a1bfdfa90ed1]
name                : "eth22"

_uuid               : 316ef777-a87b-4cad-83ab-b1e40ec1114d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0dcd0111-b533-4b7b-8510-3464872ab79e]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0dcd0111-b533-4b7b-8510-3464872ab79e
admin_state         : down
duplex              : full
ifindex             : 445
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

_uuid               : 721c67ee-91a7-4c83-989f-6a16ebc3071f
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

_uuid               : 684f749e-e420-48e3-aaa4-773281bd2303
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

_uuid               : 9509667e-158d-49c4-b245-a1bfdfa90ed1
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
commit 3c35db62d0ebdf6191c60aae0ccadbb40ac933ba
Author:     Niti Rohilla &lt;niti.rohilla@tcs.com&gt;
AuthorDate: Wed Sep 9 17:33:42 2015 +0530
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Sep 9 13:17:23 2015 -0700

    ofproto: Implement OF1.4 Group &amp; Meter change notification messages
    
    This patch adds support for Openflow1.4 Group &amp; meter change notification
    messages. In a multi controller environment, when a controller modifies the
    state of group and meter table, the request that successfully modifies this
    state is forwarded to other controllers. Other controllers are informed with
    the OFPT_REQUESTFORWARD message. Request forwarding is enabled on a per
    controller channel basis using the Set Asynchronous Configuration Message.
    
    Signed-off-by: Niti Rohilla &lt;niti.rohilla@tcs.com&gt;
    Co-authored-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
