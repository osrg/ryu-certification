---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fb767c92-653d-445c-b9a4-fa27980020c3
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b09908ae-f602-4849-bdf8-d5ea6ebc7c9c
controller          : [b8e4cd1f-ee8c-43dc-bc9d-185be732d045]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [7112e032-3f81-41b8-aabb-b464e9815c41, 88ade181-52bb-45b7-938b-90270dced83c, d74476f8-cc7b-4447-b009-14339a58b37a]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b8e4cd1f-ee8c-43dc-bc9d-185be732d045
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=242, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d74476f8-cc7b-4447-b009-14339a58b37a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ef6923f6-1be8-495d-90a4-e361415c06f4]
name                : br0

_uuid               : 88ade181-52bb-45b7-938b-90270dced83c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [09b44005-cce6-4a1d-9a04-a76d4b34bc1b]
name                : eth7

_uuid               : 7112e032-3f81-41b8-aabb-b464e9815c41
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [71694082-19fe-4b9e-a8d2-bdaa23b51cd9]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 09b44005-cce6-4a1d-9a04-a76d4b34bc1b
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
statistics          : {collisions=0, rx_bytes=343094, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=3443, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 71694082-19fe-4b9e-a8d2-bdaa23b51cd9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=98778, tx_dropped=0, tx_errors=0, tx_packets=1050}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : ef6923f6-1be8-495d-90a4-e361415c06f4
admin_state         : up
duplex              : full
ifindex             : 38
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
commit 63016faef531b23d8211d03420ab9a8f4b826b52
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Tue Jan 21 11:29:24 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jan 23 08:42:40 2014 -0800

    dpif-linux: Fix flow_dump_next annotation.
    
    The 'dpif_' parameter of dpif_linux_flow_dump_next() was marked as
    OVS_UNUSED, even though it's passed down to dpif_linux_flow_get__().
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
