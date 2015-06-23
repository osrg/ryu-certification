---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9733e306-5c89-4f60-9ae8-6390ec17e7e7
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b2925ae9-7c3e-40f8-9c53-47bb8e2f4ec5
controller          : [60bfed00-d36a-423b-bb54-1ab3d873fcd6]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [09bf4d23-232b-489d-b3e0-986087408eda, 830b5b4a-fbc6-41b7-b53e-76f54c5cc930, 85a7f3bc-bd5b-4b1d-bbdd-485ea7a05867, c2ac87ab-44a1-4f75-9c54-197638f378ed]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 60bfed00-d36a-423b-bb54-1ab3d873fcd6
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 85a7f3bc-bd5b-4b1d-bbdd-485ea7a05867
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f77758fd-4ebf-4067-a588-7eff00a5d4b7]
name                : "eth22"

_uuid               : 830b5b4a-fbc6-41b7-b53e-76f54c5cc930
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [db0663bd-f308-4bb9-8201-7ebbdf0e380e]
name                : "eth23"

_uuid               : 09bf4d23-232b-489d-b3e0-986087408eda
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0326aea8-6643-40ba-93ef-d50d6ba49eaf]
name                : "eth21"

_uuid               : c2ac87ab-44a1-4f75-9c54-197638f378ed
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0de49b9f-6463-46f2-b1fb-7a6599dc4a8e]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0326aea8-6643-40ba-93ef-d50d6ba49eaf
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

_uuid               : f77758fd-4ebf-4067-a588-7eff00a5d4b7
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

_uuid               : db0663bd-f308-4bb9-8201-7ebbdf0e380e
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

_uuid               : 0de49b9f-6463-46f2-b1fb-7a6599dc4a8e
admin_state         : down
duplex              : full
ifindex             : 188
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1c218735054d30d636215f0a6cd899a156592070
Author:     Sorin Vinturis &lt;svinturis@cloudbasesolutions.com&gt;
AuthorDate: Thu Jun 18 18:37:13 2015 +0000
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Jun 23 11:45:43 2015 -0700

    datapath-windows: Return success for already existing WFP objects
    
    There are cases when the WFP callout or sublayer, being persistent
    objects, already exists when we try to register the OVS callout. In
    this cases, when trying to add again these WFP objects the return code
    is STATUS_FWP_ALREADY_EXISTS, which we are interpreting as an error.
    This is incorrect and this patch changes that.
    
    Signed-off-by: Sorin Vinturis &lt;svinturis@cloudbasesolutions.com&gt;
    Reported-by: Sorin Vinturis &lt;svinturis@cloudbasesolutions.com&gt;
    Reported-at: https://github.com/openvswitch/ovs-issues/issues/84
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
