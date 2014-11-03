---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e9d74ee2-9ced-407b-bc57-8f78d1143481
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 361d4692-549f-4599-8816-d411f9975536
controller          : [894df0de-43b9-4d14-9804-4eafd334e287]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [15a0e562-b8a5-4989-8d61-0c697137055b, 269befac-37f4-49a7-971b-2a300a65e698, 447f7315-0c01-423b-b83c-693ec05d2f71, 63ef3f40-29cb-4971-a6c4-e1460693fadd]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 894df0de-43b9-4d14-9804-4eafd334e287
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=672, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 63ef3f40-29cb-4971-a6c4-e1460693fadd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0da778d5-7301-4a1e-a39e-c52fefc0143c]
name                : eth22

_uuid               : 269befac-37f4-49a7-971b-2a300a65e698
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b05bac53-52c7-4de8-a5ec-00a6da36771f]
name                : eth21

_uuid               : 447f7315-0c01-423b-b83c-693ec05d2f71
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b3a07806-f797-4efb-80d3-2cb57c13627e]
name                : eth23

_uuid               : 15a0e562-b8a5-4989-8d61-0c697137055b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0c550306-bbc1-4451-9791-97debc7f3487]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0da778d5-7301-4a1e-a39e-c52fefc0143c
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=160494730648, tx_dropped=0, tx_errors=0, tx_packets=107045549}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b3a07806-f797-4efb-80d3-2cb57c13627e
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=14080099500, tx_dropped=0, tx_errors=0, tx_packets=9386733}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0c550306-bbc1-4451-9791-97debc7f3487
admin_state         : down
duplex              : full
ifindex             : 317
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : b05bac53-52c7-4de8-a5ec-00a6da36771f
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=270660712115, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=180549337, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 4f0b577e0c31eb2efc15fe7b88451f310003b9ba
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Oct 3 15:49:23 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Nov 3 10:25:19 2014 -0800

    xenserver: Turn on SSE and SSE2 for the build, for atomic 64-bit ops.
    
    The ovs-atomic-i586 implementation of atomic operations can implement
    64-bit atomics more efficiently when SSE is supported.  XenServer runs only
    on 64-bit capable processors, in 32-bit mode, so we know on XenServer that
    SSE and SSE2 are supported because they are architectural for amd64.  Thus,
    this commit enables SSE and SSE2 when building for XenServer to get the
    improved atomics support.
    
    I tested that this successfully adds -msse -msse2 to the compiler flags
    inside a XenServer DDK, but I didn't actually run it on a real XenServer
    install.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
