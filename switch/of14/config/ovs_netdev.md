---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4256b3a3-1178-4ecf-81e0-425e30b90c39
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 50224474-598d-4c46-882f-c82b6ba3f7d3
controller          : [5afaf6ff-88e6-41d0-8a78-c9e0b879f518]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [089e0cfe-7606-4e30-adb0-1b1399610cbb, 443d9fae-1351-4d14-83f4-f2ab0c905bc6, 515a6a60-466d-4bbf-85be-8b73188b6990, 96370861-20e8-4949-9f3f-1bc70d641c9f]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5afaf6ff-88e6-41d0-8a78-c9e0b879f518
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=977, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 515a6a60-466d-4bbf-85be-8b73188b6990
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6199a213-9833-4e0d-9fa6-e8caaf295f0d]
name                : eth21

_uuid               : 96370861-20e8-4949-9f3f-1bc70d641c9f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9f31c10c-a45c-456b-936b-55f9dea7cad5]
name                : eth22

_uuid               : 089e0cfe-7606-4e30-adb0-1b1399610cbb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bc9eba27-1ee4-461e-9b46-320b25ad58fb]
name                : eth23

_uuid               : 443d9fae-1351-4d14-83f4-f2ab0c905bc6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [faedad9f-1805-4304-8030-3992e45b92dc]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9f31c10c-a45c-456b-936b-55f9dea7cad5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1606887866, tx_dropped=0, tx_errors=0, tx_packets=35478832}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6199a213-9833-4e0d-9fa6-e8caaf295f0d
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
statistics          : {collisions=0, rx_bytes=1701129120, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=90020785, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : bc9eba27-1ee4-461e-9b46-320b25ad58fb
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=26966784, tx_dropped=0, tx_errors=0, tx_packets=11471908}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : faedad9f-1805-4304-8030-3992e45b92dc
admin_state         : down
duplex              : full
ifindex             : 662
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ccf4378615e93618e6ab8423fa1400b40876df91
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Tue Jun 24 20:56:57 2014 +0900
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Tue Jun 24 16:02:02 2014 -0700

    datapath: Add basic MPLS support to kernel
    
    Allow datapath to recognize and extract MPLS labels into flow keys
    and execute actions which push, pop, and set labels on packets.
    
    Based heavily on work by Leo Alterman, Ravi K, Isaku Yamahata and Joe Stringer.
    
    Cc: Ravi K &lt;rkerur@gmail.com&gt;
    Cc: Leo Alterman &lt;lalterman@nicira.com&gt;
    Cc: Isaku Yamahata &lt;yamahata@valinux.co.jp&gt;
    Cc: Joe Stringer &lt;joe@wand.net.nz&gt;
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
