---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
bcba2e12-9490-4161-a0ba-d75b54fc27c0
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
_uuid               : be7f3eaa-6e3d-4933-b05e-3f8a9e336210
controller          : [7868d0bb-ada1-4b7d-9f40-25c4376323d0]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [06ceaafe-3c52-443c-8439-4ed4c8d51dc3, 2f221530-2e5c-4c6d-89ae-d0a294f1aa95, 2fc7e815-27e3-4739-9fca-d4e9565bbc96]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7868d0bb-ada1-4b7d-9f40-25c4376323d0
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2f221530-2e5c-4c6d-89ae-d0a294f1aa95
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bf7f23c4-9c27-4418-98e7-9affdc96bb67]
name                : eth8

_uuid               : 2fc7e815-27e3-4739-9fca-d4e9565bbc96
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [59404e33-e5cc-4041-b05d-fac1a561b89a]
name                : eth7

_uuid               : 06ceaafe-3c52-443c-8439-4ed4c8d51dc3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ddd6e0d8-5df5-44e5-8241-f388dd0c83ee]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : bf7f23c4-9c27-4418-98e7-9affdc96bb67
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

_uuid               : ddd6e0d8-5df5-44e5-8241-f388dd0c83ee
admin_state         : up
duplex              : full
ifindex             : 588
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

_uuid               : 59404e33-e5cc-4041-b05d-fac1a561b89a
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
