---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3ef02bd2-4f4f-477d-98af-5e3bf10af66c
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 88640c9d-57ce-4a24-8bd0-4278ebf066c2
controller          : [80e1b11f-638f-452c-9bdc-fa68d3b03074]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [9884e201-948e-443d-8fa8-fdb534cfeac4, c5125a0a-f57b-4285-908c-0024998438cb, eab80330-4ba5-44e0-bbd8-9efc084faa61]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 80e1b11f-638f-452c-9bdc-fa68d3b03074
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=377, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : eab80330-4ba5-44e0-bbd8-9efc084faa61
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c487fecd-9c12-4f2f-bbf2-441d2c14c9a6]
name                : eth7

_uuid               : 9884e201-948e-443d-8fa8-fdb534cfeac4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [19be362d-a44c-4ddf-86f4-1e84b1d39d8b]
name                : br0

_uuid               : c5125a0a-f57b-4285-908c-0024998438cb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [99d34c23-9361-4153-912d-94a887abd6bc]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 19be362d-a44c-4ddf-86f4-1e84b1d39d8b
admin_state         : up
duplex              : full
ifindex             : 451
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

_uuid               : c487fecd-9c12-4f2f-bbf2-441d2c14c9a6
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
statistics          : {collisions=0, rx_bytes=3061662390, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72619009, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 99d34c23-9361-4153-912d-94a887abd6bc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3241060, tx_dropped=0, tx_errors=0, tx_packets=34586}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 72310b041cfa7d8e2ee5fb585348223ac7c22497
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Wed Mar 5 16:56:05 2014 -0800
Commit:     Justin Pettit &lt;jpettit@nicira.com&gt;
CommitDate: Fri Mar 7 18:33:21 2014 -0800

    upcall: Configure datapath max-idle through ovs-vsctl.
    
    This patch adds a new configuration option, max-idle to the
    Open_vSwitch other-config column. This sets how long datapath flows
    are cached in the datapath before revalidators expire them.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Signed-off-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
