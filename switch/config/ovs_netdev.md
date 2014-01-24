---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3b714a3f-923a-43e4-a53d-99db870ce6e8
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 774ff66b-8a54-43da-a33c-30503bbcbd5d
controller          : [8787f0c3-19ab-4701-bfd6-aa4232148d62]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [9399cb4a-67d4-43fe-9645-731a9b546b75, a8339a03-0865-4a6b-b9c3-ec83cdd047fb, d8399ed1-3be8-496f-8787-fa93bda918d2]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8787f0c3-19ab-4701-bfd6-aa4232148d62
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=296, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d8399ed1-3be8-496f-8787-fa93bda918d2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ed043d94-3346-4599-a1a7-abf2d87a6c7c]
name                : br0

_uuid               : 9399cb4a-67d4-43fe-9645-731a9b546b75
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [95be66cc-7dc1-44f7-9ccf-2f47d4702eeb]
name                : eth7

_uuid               : a8339a03-0865-4a6b-b9c3-ec83cdd047fb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b7bb6dcc-d329-4dc5-b715-db9c6ef6d3a8]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ed043d94-3346-4599-a1a7-abf2d87a6c7c
admin_state         : up
duplex              : full
ifindex             : 61
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : b7bb6dcc-d329-4dc5-b715-db9c6ef6d3a8
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=177746, tx_dropped=0, tx_errors=0, tx_packets=1894}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 95be66cc-7dc1-44f7-9ccf-2f47d4702eeb
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=667042, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=6727, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fa5b8c6724f3fdfd290c414ec194c8948e57e775
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Mon Jan 6 13:12:21 2014 -0800
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Fri Jan 24 07:48:18 2014 -0800

    syslog: Add LOG_LOCALX definitions.
    
    LOG_LOCAL0 is used in lib/vlog.c.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
