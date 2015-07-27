---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8bdd94e1-5939-4b1a-8eba-04ca608c48a6
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ce5ace31-b451-4a09-b75b-dd23085a222f
controller          : [b6b38d01-36e0-4f2a-b79d-40ea52077c87]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [27877fa2-28b7-46eb-a522-e72460cbda5e, 3db54b2d-1648-4d82-908e-e0610e519dd2, aca3c997-f0e8-494b-837b-06ace5286ade, b94904a0-abeb-4555-96e3-d0ca38db528f]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b6b38d01-36e0-4f2a-b79d-40ea52077c87
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b94904a0-abeb-4555-96e3-d0ca38db528f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e7713547-126f-4088-9ac3-f99bf75576bc]
name                : "eth23"

_uuid               : 3db54b2d-1648-4d82-908e-e0610e519dd2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [827fbf2b-148b-42b4-90c2-4929d734a4f3]
name                : "eth21"

_uuid               : 27877fa2-28b7-46eb-a522-e72460cbda5e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2e218bd6-2678-40f7-9b7d-d11d836d43b7]
name                : "br0"

_uuid               : aca3c997-f0e8-494b-837b-06ace5286ade
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d44ba079-50d0-4715-9730-2a3eb6bd3618]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d44ba079-50d0-4715-9730-2a3eb6bd3618
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

_uuid               : 2e218bd6-2678-40f7-9b7d-d11d836d43b7
admin_state         : down
duplex              : full
ifindex             : 291
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

_uuid               : e7713547-126f-4088-9ac3-f99bf75576bc
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

_uuid               : 827fbf2b-148b-42b4-90c2-4929d734a4f3
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
commit 980904823303ef02af605e62a30c9bebda25f1ef
Author:     Niti Rohilla &lt;niti.rohilla@tcs.com&gt;
AuthorDate: Thu Jul 23 17:05:44 2015 +0530
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Jul 27 10:15:28 2015 -0700

    ofproto: Implement OF1.4 Set/Get asynchronous configuration messages.
    
    This patch adds support for Openflow1.4 set/get asynchronous configuration
    messages. OpenVSwitch already supports set/get asynchronous configuration
    messages for Openflow1.3. In this patch OFPT_SET_ASYNC_CONFIG message
    allows the controllers to set the configuration for OFPT_ROLE_STATUS,
    OFPT_TABLE_STATUS and OFPT_REQUESTFORWARD in addition to the Openflow1.3
    messages. In a OFPT_SET_ASYNC, only the properties that shall be changed
    need to be included, properties that are omitted from the message are
    unchanged.
    
    The OFPT_GET_ASYNC_CONFIG is used to query the asynchronous configuration
    of switch. In a OFPT_GET_ASYNC_REPLY message, all properties must be
    included.
    
    According to Openflow1.4 the initial configuration shall be:
    
       - In the “master” or “equal” role, enable all OFPT_PACKET_IN messages,
         except those with reason OFPR_INVALID_TTL, enable all OFPT_PORT_STATUS
         and OFPT_FLOW_REMOVED messages, and disable all OFPT_ROLE_STATUS,
         OFPT_TABLE_STATUS and OFPT_REQUESTFORWARD messages.
    
       - In the “slave” role, enable all OFPT_PORT_STATUS messages and disable
         all OFPT_PACKET_IN, OFPT_FLOW_REMOVED, OFPT_ROLE_STATUS,
         OFPT_TABLE_STATUS and OFPT_REQUESTFORWARD messages.
    
    Signed-off-by: Niti Rohilla &lt;niti.rohilla@tcs.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
