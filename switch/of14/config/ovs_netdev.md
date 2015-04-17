---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ed87fd5f-4ec4-4112-b029-c137f0bbaf70
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 91e0268f-ddbe-441a-a176-a5746faa5f4e
controller          : [dbae6a54-79ac-4f44-90dd-a2ecd3b2d0d8]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [018d9a48-ba9a-48f9-8f91-e608865f55d4, 7e4e6d02-dd01-4ccb-b718-89469fa5791d, b38236e0-ede9-4fa3-81b1-58914fd0c2e3, f36fa1a3-9037-43c7-9ee8-278f2c2e7b0d]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : dbae6a54-79ac-4f44-90dd-a2ecd3b2d0d8
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="652", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 018d9a48-ba9a-48f9-8f91-e608865f55d4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [979163ea-e049-40f1-aead-d6ec7594b110]
name                : "eth22"

_uuid               : b38236e0-ede9-4fa3-81b1-58914fd0c2e3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b8b7a571-4664-426d-9bc8-aa7715a811a1]
name                : "br0"

_uuid               : 7e4e6d02-dd01-4ccb-b718-89469fa5791d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5dbef48f-48f4-4173-8b6c-06b69d947d59]
name                : "eth23"

_uuid               : f36fa1a3-9037-43c7-9ee8-278f2c2e7b0d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6ac2aa5f-236a-4bb0-8a57-b2370ca223bb]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b8b7a571-4664-426d-9bc8-aa7715a811a1
admin_state         : down
duplex              : full
ifindex             : 917
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

_uuid               : 979163ea-e049-40f1-aead-d6ec7594b110
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=630732240845, tx_dropped=0, tx_errors=0, tx_packets=420655351}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 5dbef48f-48f4-4173-8b6c-06b69d947d59
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=41896911000, tx_dropped=0, tx_errors=0, tx_packets=27931274}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 6ac2aa5f-236a-4bb0-8a57-b2370ca223bb
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
statistics          : {collisions=0, rx_bytes=1232894584411, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=822309099, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1c79befb3cdf1dd861f463c6f58762bc34f6784c
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Apr 17 10:06:17 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Apr 17 10:06:17 2015 -0700

    perf-counter: Remove unused vlog module.
    
    Otherwise Clang warns about an unused variable.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
