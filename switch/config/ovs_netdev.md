---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
df7d505b-ac94-4cfd-bb23-1f49c4e38173
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
_uuid               : b24d297c-492d-431c-b915-30b39c44a11d
controller          : [6c15f9bf-66f7-4e56-9f53-71f98c212912]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [20db77e2-58c0-46cf-bbd4-6919a80821dc, 5f6b31e4-b559-483a-9eea-7d9780a3a946, a6f2d6bb-8f9a-4bb7-8941-a0f4e2a61cf5]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6c15f9bf-66f7-4e56-9f53-71f98c212912
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5f6b31e4-b559-483a-9eea-7d9780a3a946
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a8364fd9-1c17-49a4-aea0-14667c8b281b]
name                : eth7

_uuid               : 20db77e2-58c0-46cf-bbd4-6919a80821dc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5d1f41f3-9244-4e33-8145-a5fb8191fecb]
name                : br0

_uuid               : a6f2d6bb-8f9a-4bb7-8941-a0f4e2a61cf5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [85bcedfc-abb6-424d-9170-a1e8c16abd4b]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 85bcedfc-abb6-424d-9170-a1e8c16abd4b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4363182, tx_dropped=0, tx_errors=0, tx_packets=46530}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : a8364fd9-1c17-49a4-aea0-14667c8b281b
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
statistics          : {collisions=0, rx_bytes=3065453892, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72657451, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 5d1f41f3-9244-4e33-8145-a5fb8191fecb
admin_state         : up
duplex              : full
ifindex             : 594
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
commit 06f64d032ab82237b4ff7d92f6d6328869d70931
Author:     Justin Pettit &lt;jpettit@nicira.com&gt;
AuthorDate: Tue Mar 18 14:29:17 2014 -0700
Commit:     Justin Pettit &lt;jpettit@nicira.com&gt;
CommitDate: Tue Mar 18 14:29:17 2014 -0700

    tests: Fix small typo in OpenFlow in ofproto tests.
    
    Signed-off-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
