---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4260dd9b-9297-482c-9ef2-e15caa354b7d
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d8c8e408-3c62-46fc-976b-1014ad1d9221
controller          : [a412c46d-902a-4ae2-9f61-cd776e3f70dd]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [38aca520-3aeb-462e-bcac-639504f64b61, 82a705d0-868f-456f-9329-64f0d87e06fa, cd96a0a7-2d89-4a08-b8ab-2dcfc51d62f7, d0a2648a-d84f-446e-9665-ace94f4b0eff]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a412c46d-902a-4ae2-9f61-cd776e3f70dd
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 38aca520-3aeb-462e-bcac-639504f64b61
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bfbb7afd-5c3f-483d-82dd-2a394d304195]
name                : "eth23"

_uuid               : 82a705d0-868f-456f-9329-64f0d87e06fa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4257b8d6-e6e9-4712-86ba-0ce5d2eba572]
name                : "br0"

_uuid               : d0a2648a-d84f-446e-9665-ace94f4b0eff
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b5b4d19d-23e4-4ebb-a265-758af53eacb0]
name                : "eth22"

_uuid               : cd96a0a7-2d89-4a08-b8ab-2dcfc51d62f7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f3db699b-909b-4a62-9fd2-f1657b9dd8db]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b5b4d19d-23e4-4ebb-a265-758af53eacb0
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

_uuid               : bfbb7afd-5c3f-483d-82dd-2a394d304195
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

_uuid               : 4257b8d6-e6e9-4712-86ba-0ce5d2eba572
admin_state         : down
duplex              : full
ifindex             : 289
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

_uuid               : f3db699b-909b-4a62-9fd2-f1657b9dd8db
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
