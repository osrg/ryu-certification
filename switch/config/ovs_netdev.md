---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
73ff3ae7-d26d-420c-87ef-8eff9c940d1e
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
_uuid               : a5f77ce3-8c50-44bb-9931-dc813155daed
controller          : [989366d5-1179-4a33-80db-03eb3d83fee4]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3cea6c25-237a-4565-a036-56bef26d0800, 6c13e717-c640-48ee-a522-e2f61e7c6d64, 87b9bc0d-2b04-477f-ba93-68aa6e5dcb81, be81f065-8cc5-48a6-b8dc-8bba316a1799]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 989366d5-1179-4a33-80db-03eb3d83fee4
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : be81f065-8cc5-48a6-b8dc-8bba316a1799
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9218e442-9101-44be-ab89-56b5125fa11c]
name                : "eth22"

_uuid               : 3cea6c25-237a-4565-a036-56bef26d0800
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4587197e-9eec-4c3f-bfbe-bad047586e7c]
name                : "eth23"

_uuid               : 87b9bc0d-2b04-477f-ba93-68aa6e5dcb81
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f71a27ff-9440-4f8e-a3ce-b0b740964e9d]
name                : "eth21"

_uuid               : 6c13e717-c640-48ee-a522-e2f61e7c6d64
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [92d73f40-8204-42d2-b8c6-c159e191891c]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 92d73f40-8204-42d2-b8c6-c159e191891c
admin_state         : down
duplex              : full
ifindex             : 732
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

_uuid               : 4587197e-9eec-4c3f-bfbe-bad047586e7c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7696948500, tx_dropped=0, tx_errors=0, tx_packets=5131299}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9218e442-9101-44be-ab89-56b5125fa11c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30014465684, tx_dropped=0, tx_errors=0, tx_packets=20036351}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f71a27ff-9440-4f8e-a3ce-b0b740964e9d
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
statistics          : {collisions=0, rx_bytes=44034227310, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29415081, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 02ab4b1a6a173979a51cabd7000a34546d517e60
Author:     mweglicx &lt;michalx.weglicki@intel.com&gt;
AuthorDate: Wed Dec 23 10:20:22 2015 +0000
Commit:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
CommitDate: Mon Jan 25 18:37:17 2016 -0800

    Update relevant artifacts to add support for DPDK v2.2.0.
    
    Following changes have been applied:
     - INSTALL.DPDK.md: change DPDK version number,
     - build.sh: change DPDK version number.
    
    Signed-off-by: Michal Weglicki &lt;michalx.weglicki@intel.com&gt;
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>
