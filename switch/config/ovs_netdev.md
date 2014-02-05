---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
774a10b1-d7dc-4b35-89b0-80fa6fcc3664
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
_uuid               : dcc5fab9-2521-4110-aa02-4d1b7c680400
controller          : [57f12863-0fc5-4f0c-b695-8a9dca653867]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [150ff065-5fb5-4b64-b0c7-0037e90e4b4b, 6f7280b9-4004-4716-927e-6d13db0e5b14, 9a8d742c-1bf3-4bdb-96b6-cf63f46a3c24]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 57f12863-0fc5-4f0c-b695-8a9dca653867
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=297, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9a8d742c-1bf3-4bdb-96b6-cf63f46a3c24
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2b9b1b1d-0f3a-4495-8ed8-df5c3c329338]
name                : eth8

_uuid               : 6f7280b9-4004-4716-927e-6d13db0e5b14
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c14b68c8-8779-4203-b217-8011d9d88a34]
name                : eth7

_uuid               : 150ff065-5fb5-4b64-b0c7-0037e90e4b4b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [96f34ac7-efff-40c3-881a-d17c8a8d3b6c]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c14b68c8-8779-4203-b217-8011d9d88a34
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
statistics          : {collisions=0, rx_bytes=3055012175, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72551754, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 2b9b1b1d-0f3a-4495-8ed8-df5c3c329338
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1164228, tx_dropped=0, tx_errors=0, tx_packets=12445}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 96f34ac7-efff-40c3-881a-d17c8a8d3b6c
admin_state         : up
duplex              : full
ifindex             : 163
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
commit 978188b242c8900f2a598f8d5bb233d9155ebf36
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Tue Feb 4 21:58:03 2014 -0800
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Tue Feb 4 21:58:03 2014 -0800

    datapath: Fix kernel style issues.
    
    Suggested-by: Sergei Shtylyov &lt;sergei.shtylyov@cogentembedded.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
