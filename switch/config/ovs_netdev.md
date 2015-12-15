---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1ea62c74-6d5e-4093-acdc-6d6d9104b715
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8224f5cc-d88a-448f-969c-377e2dbfb75e
controller          : [bca7e5b3-9c2a-4868-89b6-fc8c3e80b39f]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [4462e0b2-d349-40f5-a3d5-843d9faeb59e, 9a26d4a0-0ea5-470b-b312-da3b7578a5c8, d0dfac49-919d-4f1f-95d8-8514d6e0a6cc, f0f9d3b3-7aa2-4294-a2f7-eedd689dabd5]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : bca7e5b3-9c2a-4868-89b6-fc8c3e80b39f
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="672", sec_since_disconnect="6", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9a26d4a0-0ea5-470b-b312-da3b7578a5c8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9298a535-d4e4-4fe3-8a87-ad084176a276]
name                : "eth21"

_uuid               : d0dfac49-919d-4f1f-95d8-8514d6e0a6cc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [61d3e205-b529-4604-b1b6-5edd1a55ab95]
name                : "eth22"

_uuid               : 4462e0b2-d349-40f5-a3d5-843d9faeb59e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ef01c6ec-b8ea-4c17-a84d-78ab3aa6b6e5]
name                : "eth23"

_uuid               : f0f9d3b3-7aa2-4294-a2f7-eedd689dabd5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [57b36f10-7fb3-4faf-8b46-86cb45833e0e]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 57b36f10-7fb3-4faf-8b46-86cb45833e0e
admin_state         : down
duplex              : full
ifindex             : 684
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

_uuid               : ef01c6ec-b8ea-4c17-a84d-78ab3aa6b6e5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6556353000, tx_dropped=0, tx_errors=0, tx_packets=4370902}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9298a535-d4e4-4fe3-8a87-ad084176a276
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
statistics          : {collisions=0, rx_bytes=42512963243, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28392360, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 61d3e205-b529-4604-b1b6-5edd1a55ab95
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29330134221, tx_dropped=0, tx_errors=0, tx_packets=19575966}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 398e182e365d1709a0d085bdee365ff3c19ca001
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Thu Dec 10 11:16:51 2015 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Tue Dec 15 00:47:44 2015 -0800

    datapath-windows: remove ASSERT in OvsDoFlowLookupOutput&#40;&#41;
    
    We needed this ASSERT earlier to catch unexpected cases. This code seems
    to be fairly stable, and we can remove the ASSERT.
    
    It is annoying to be hitting this ASSERT while changing the internal
    adapter properties.
    
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
