---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0c2deb72-2018-465f-86b8-94221ba54075
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8a54a3de-4ee9-4537-8302-371eaf2e323d
controller          : [e7318d43-c2a7-49a1-b804-1bfa2cdde350]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [13aa1f9a-d4a4-4936-9d29-b712e94594bb, 153f6f54-a2fd-4e96-acea-d59469a8ef52, 9ce56bd9-2311-4c35-a4ca-afffe68b4a06, ff897b8f-d786-4dfc-8ec8-2c57d2006f4d]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e7318d43-c2a7-49a1-b804-1bfa2cdde350
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 153f6f54-a2fd-4e96-acea-d59469a8ef52
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [47b33d97-96e0-4198-814f-68b04103359f]
name                : "eth21"

_uuid               : 9ce56bd9-2311-4c35-a4ca-afffe68b4a06
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [281a798b-758e-4027-a05e-f64bf50ffc7c]
name                : "eth23"

_uuid               : 13aa1f9a-d4a4-4936-9d29-b712e94594bb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9226927c-ff73-458e-a450-ea26b74a176e]
name                : "eth22"

_uuid               : ff897b8f-d786-4dfc-8ec8-2c57d2006f4d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ada354a2-6e2e-42ea-9a5a-d5ead8eecab6]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9226927c-ff73-458e-a450-ea26b74a176e
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

_uuid               : ada354a2-6e2e-42ea-9a5a-d5ead8eecab6
admin_state         : down
duplex              : full
ifindex             : 202
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

_uuid               : 281a798b-758e-4027-a05e-f64bf50ffc7c
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

_uuid               : 47b33d97-96e0-4198-814f-68b04103359f
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
commit 5bb08b0ef605a9b164399bd74a194ae1b921c3ea
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Mon Jun 22 14:23:37 2015 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Fri Jun 26 14:18:07 2015 -0700

    tunneling: Userspace datapath support for Geneve options.
    
    Currently the userspace datapath only supports Geneve in a
    basic mode - without options - since the rest of userspace
    previously didn't support options either. This enables the
    userspace datapath to send and receive options as well.
    
    The receive path for extracting the tunnel options isn't entirely
    optimal because it does a lookup on the options on a per-packet
    basis, rather than per-flow like the kernel does. This is not
    as straightforward to do in the userspace datapath since there
    is no translation step between packet formats used in packet vs.
    flow lookup. This can be optimized in the future and in the
    meantime option support is still useful for testing and simulation.
    
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
