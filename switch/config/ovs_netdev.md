---
layout: default
title: ovs_netdev - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
78fc1ed8-7986-45ca-a039-4d7a967c31dd
    Bridge "br0"
        Controller "tcp:10.24.150.30"
            is_connected: true
        fail_mode: secure
        Port "eth7"
            Interface "eth7"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth8"
            Interface "eth8"

$ sudo ovs-vsctl list Bridge
_uuid               : b7bd37bf-87db-4689-9d04-f723470b7310
controller          : [02d138f7-dbbf-451f-b6dc-210390aa4ea6]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [b5f3de25-22b8-443b-bbf6-3f645752ef13, db74f111-4628-435c-a03b-437f783f2d14, fe16c2bb-9b6a-4a26-bb47-a2d69ca47398]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 02d138f7-dbbf-451f-b6dc-210390aa4ea6
is_connected        : true
role                : other
status              : {last_error="Connection refused", sec_since_connect="121", sec_since_disconnect="123", state=ACTIVE}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : b5f3de25-22b8-443b-bbf6-3f645752ef13
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ac81f0fe-fc87-4c64-b547-78230f7fd9dc]
name                : "eth7"

_uuid               : db74f111-4628-435c-a03b-437f783f2d14
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [626cfcf9-49d6-4967-99ad-a2f51c34f8ea]
name                : "br0"

_uuid               : fe16c2bb-9b6a-4a26-bb47-a2d69ca47398
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [833e0acd-4d5c-449d-91a0-ca5ff04e1dcd]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : 626cfcf9-49d6-4967-99ad-a2f51c34f8ea
admin_state         : up
ifindex             : 43
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 833e0acd-4d5c-449d-91a0-ca5ff04e1dcd
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:ec"
mtu                 : 1550
name                : "eth8"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=11040, tx_dropped=0, tx_errors=0, tx_packets=119}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : ac81f0fe-fc87-4c64-b547-78230f7fd9dc
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "eth7"
ofport              : 1
statistics          : {collisions=0, rx_bytes=21744, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=228, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a6da6967977daddbb68fbe170429f0b5385bde94
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Dec 24 08:37:32 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Dec 30 09:43:27 2013 -0800

    Makefile.am: Always use C locale for "sort" and "comm".
    
    Otherwise, if the user changes locales between running the "dist-hook-git"
    and "distfiles" targets (e.g. in different invocations of "make"), then
    the "dist-hook-git" target might falsely report that the distribution is
    missing files.
    
    Reported-by: John Darrington &lt;john@darrington.wattle.id.au&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
