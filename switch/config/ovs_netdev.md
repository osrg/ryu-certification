---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6d99d5e3-2056-41b0-b8e5-04ff51f4618e
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8f19cc53-5954-43cf-ac8b-c71d404dcd00
controller          : [1c51430b-e996-4bf0-a288-05bb2fbab231]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [35327156-1e9e-463c-aa02-d604d7391a94, 4e665547-97d9-48a0-9273-bdbf6a6992d1, d99a72aa-47b1-4d76-8fda-c199adb0f563]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 1c51430b-e996-4bf0-a288-05bb2fbab231
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=382, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d99a72aa-47b1-4d76-8fda-c199adb0f563
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7277a809-a930-4df0-a2ef-119377c5c04d]
name                : eth8

_uuid               : 35327156-1e9e-463c-aa02-d604d7391a94
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0fc124c6-9976-4db2-9a7e-f16e24591704]
name                : eth7

_uuid               : 4e665547-97d9-48a0-9273-bdbf6a6992d1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7b1d153b-1777-4b29-881b-9d5378347186]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7277a809-a930-4df0-a2ef-119377c5c04d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4521014, tx_dropped=0, tx_errors=0, tx_packets=48211}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 0fc124c6-9976-4db2-9a7e-f16e24591704
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
statistics          : {collisions=0, rx_bytes=3065996532, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72662962, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 7b1d153b-1777-4b29-881b-9d5378347186
admin_state         : up
duplex              : full
ifindex             : 614
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
commit f1946fbe8300e906c30491387e565f3b58d7f049
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Wed Mar 19 10:42:08 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Wed Mar 19 10:53:39 2014 -0700

    ovs-rcu: Call ovsrcu_init() in ovsrcu_quiesce().
    
    This commit fixes a bug introduced by 0f2ea848(ovs-rcu: New library.).
    It is possible that ovsrcu_quiesce() is called before ovsrcu_init().
    So, it is necessary to call ovsrcu_init() in ovsrcu_quiesce().
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
