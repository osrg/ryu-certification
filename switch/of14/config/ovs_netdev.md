---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
de36c4b8-5e2f-45c3-8820-4f3c4fad7580
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 53d41424-2c44-4cdf-8b29-31ad49fd0386
controller          : [cadecc9d-ff05-4c3f-af5f-82737a02877b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [281e8996-3139-487c-b24e-5029df70aa81, 3480e673-8e63-4956-bdd3-68004a360248, 48a09f7c-ff85-4fbe-9267-d556548aac87, ce0705d2-3433-43d3-a0ea-6fb8b4f16e07]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : cadecc9d-ff05-4c3f-af5f-82737a02877b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 48a09f7c-ff85-4fbe-9267-d556548aac87
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4be1f82f-8090-456c-89ea-51d3f69386ab]
name                : "eth22"

_uuid               : 281e8996-3139-487c-b24e-5029df70aa81
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [00a3aedc-3e4e-41ac-bf7a-856ecaf5a894]
name                : "br0"

_uuid               : ce0705d2-3433-43d3-a0ea-6fb8b4f16e07
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6c9d1463-072e-4f20-99f5-14795ad488bb]
name                : "eth21"

_uuid               : 3480e673-8e63-4956-bdd3-68004a360248
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [758975bb-7e62-4083-9884-ce4259bb54af]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 00a3aedc-3e4e-41ac-bf7a-856ecaf5a894
admin_state         : down
duplex              : full
ifindex             : 443
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

_uuid               : 4be1f82f-8090-456c-89ea-51d3f69386ab
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

_uuid               : 758975bb-7e62-4083-9884-ce4259bb54af
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

_uuid               : 6c9d1463-072e-4f20-99f5-14795ad488bb
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
