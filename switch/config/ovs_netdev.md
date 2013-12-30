---
layout: default
title: ovs_netdev - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
06afb02d-2e2c-4b00-91b6-54bdaee00f38
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth7"
            Interface "eth7"
        Port "eth8"
            Interface "eth8"

$ sudo ovs-vsctl list Bridge
_uuid               : 1e06cee5-597a-4f86-9fb6-b98ff5dee3b6
controller          : [9b2bfdfe-f184-4183-b62f-f7bfb045c04f]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2a0096fa-a7b0-4ae0-ac91-e2e9a15a47cf, 95950709-49f6-4ab4-ac97-863a85b60929, 9c8a5494-8ebd-4eae-9565-96e4d189ae20]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 9b2bfdfe-f184-4183-b62f-f7bfb045c04f
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="297", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 9c8a5494-8ebd-4eae-9565-96e4d189ae20
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [87bf298e-17f3-4cb8-8dcc-d0bfc739282c]
name                : "eth8"

_uuid               : 95950709-49f6-4ab4-ac97-863a85b60929
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [32fb95a7-3239-453c-9fc6-e68a4c48c3a7]
name                : "eth7"

_uuid               : 2a0096fa-a7b0-4ae0-ac91-e2e9a15a47cf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f5761908-63ae-44cb-951c-bdc07345f5ad]
name                : "br0"

$ sudo ovs-vsctl list Interface
_uuid               : f5761908-63ae-44cb-951c-bdc07345f5ad
admin_state         : up
duplex              : full
ifindex             : 41
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : 87bf298e-17f3-4cb8-8dcc-d0bfc739282c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=150700, tx_dropped=0, tx_errors=0, tx_packets=1628}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 32fb95a7-3239-453c-9fc6-e68a4c48c3a7
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
statistics          : {collisions=0, rx_bytes=373307, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=3844, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
