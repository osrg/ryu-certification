---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
cf6f03b3-bb83-400e-a2f8-86135144db57
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
_uuid               : a39b23d4-f2f6-46a2-9967-aa0c373decb4
controller          : [47d61622-353e-4b38-943b-b405f3b51510]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [3ba84989-a16f-48ba-b53b-0157476dcf2e, 5aa61341-30c4-4404-a75b-fdb80e398d73, 878f0e9d-f5db-45cc-bcdb-1e75eafac7cb]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 47d61622-353e-4b38-943b-b405f3b51510
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=241, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5aa61341-30c4-4404-a75b-fdb80e398d73
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dc31c745-477b-4c3f-b545-bf8e01d02161]
name                : eth8

_uuid               : 3ba84989-a16f-48ba-b53b-0157476dcf2e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aab08b17-435d-44cb-b3b7-5b2b0e935002]
name                : eth7

_uuid               : 878f0e9d-f5db-45cc-bcdb-1e75eafac7cb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c1c23ddd-3585-4aa2-928f-21d987858c49]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : dc31c745-477b-4c3f-b545-bf8e01d02161
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

_uuid               : c1c23ddd-3585-4aa2-928f-21d987858c49
admin_state         : up
duplex              : full
ifindex             : 48
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

_uuid               : aab08b17-435d-44cb-b3b7-5b2b0e935002
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
statistics          : {collisions=0, rx_bytes=422849, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=4253, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9c8ad495ec332a29b4e101c00b0b0341631a4d20
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Tue Jan 21 11:29:26 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jan 23 11:31:06 2014 -0800

    netlink: Rename 'dump-&gt;seq' to 'dump-&gt;nl_seq'
    
    An upcoming patch will introduce another, completely unrelated seq to
    'struct nl_dump'. Giving this one a better name should reduce confusion.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
