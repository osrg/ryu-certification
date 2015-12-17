---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
bc8e0c91-a40d-4ba6-8b6c-d7011e6dafa2
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d5ddd97d-364f-42e3-84d9-d3e3cfd3d38c
controller          : [1562dfcf-1936-4ad9-9b14-96a6ac09ab1e]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [09d38518-2472-4426-80ec-1b7b24f7f0bc, 5308ef93-2d8a-4f0e-9bfb-19c4a1d66708, a6ad86b5-aba6-4e9c-a9ce-f5377f3bb05b, dc74a062-ff68-4371-a3b0-197eadd2da46]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 1562dfcf-1936-4ad9-9b14-96a6ac09ab1e
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="6", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 09d38518-2472-4426-80ec-1b7b24f7f0bc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4f3122dc-f580-45b2-a4e6-2edbe256fad9]
name                : "eth23"

_uuid               : a6ad86b5-aba6-4e9c-a9ce-f5377f3bb05b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a9253d09-efc0-4b64-89ea-6f5bb5c7d489]
name                : "br0"

_uuid               : dc74a062-ff68-4371-a3b0-197eadd2da46
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c6e451b3-8482-45ff-8f02-c5efc5926b18]
name                : "eth22"

_uuid               : 5308ef93-2d8a-4f0e-9bfb-19c4a1d66708
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [22180c90-2de0-4abd-9d50-8189831eb5d5]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4f3122dc-f580-45b2-a4e6-2edbe256fad9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6731956500, tx_dropped=0, tx_errors=0, tx_packets=4487971}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 22180c90-2de0-4abd-9d50-8189831eb5d5
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
statistics          : {collisions=0, rx_bytes=42746988025, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28549692, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a9253d09-efc0-4b64-89ea-6f5bb5c7d489
admin_state         : down
duplex              : full
ifindex             : 692
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

_uuid               : c6e451b3-8482-45ff-8f02-c5efc5926b18
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29435271487, tx_dropped=0, tx_errors=0, tx_packets=19646699}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e7b438dc3014c42aa5a0b4436ec4a67790f06d39
Author:     Gurucharan Shetty &lt;guru@ovn.org&gt;
AuthorDate: Tue Dec 15 08:27:15 2015 -0800
Commit:     Gurucharan Shetty &lt;guru@ovn.org&gt;
CommitDate: Wed Dec 16 10:26:24 2015 -0800

    ovn-ctl: Add daemon status functions.
    
    Signed-off-by: Gurucharan Shetty &lt;guru@ovn.org&gt;
    Acked-by: Russell Bryant &lt;russell@ovn.org&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
