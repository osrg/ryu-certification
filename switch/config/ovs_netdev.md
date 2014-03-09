---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
60e17df4-366c-42ac-9def-8029ce40bfd1
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 2747d5a9-e378-4d32-90ca-dd8f0ab49bb4
controller          : [e1219f15-062c-4125-b65a-630d7a5ac81a]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [882efec3-839f-4e4e-b9b3-dbfb0d456d98, a86bd8ff-5438-4434-8f57-39e2d3ab56d9, d9bfd688-8e98-41a0-8987-126aea933910]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e1219f15-062c-4125-b65a-630d7a5ac81a
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=372, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d9bfd688-8e98-41a0-8987-126aea933910
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [93282572-6885-4233-b0a1-6ac2d05b896e]
name                : eth8

_uuid               : 882efec3-839f-4e4e-b9b3-dbfb0d456d98
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7a78583e-d2df-4a48-a6f0-a269088df13e]
name                : br0

_uuid               : a86bd8ff-5438-4434-8f57-39e2d3ab56d9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [76d87c78-71f2-4d17-af75-7764e511cc66]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 76d87c78-71f2-4d17-af75-7764e511cc66
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
statistics          : {collisions=0, rx_bytes=3061800508, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72620405, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 93282572-6885-4233-b0a1-6ac2d05b896e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3283372, tx_dropped=0, tx_errors=0, tx_packets=35036}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 7a78583e-d2df-4a48-a6f0-a269088df13e
admin_state         : up
duplex              : full
ifindex             : 456
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
