---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4d5c593d-f560-4189-9a80-a1b45e270eaa
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 90532976-1444-4a28-a84c-e3477ea45b9d
controller          : [b85d74ba-41fa-4ec8-beb6-e0082fd1f197]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0280733f-d542-4220-8602-9e5706aea08a, 457aa162-ca34-44b2-af9d-baaab0b628f2, 8da6292e-15c9-4159-a62d-7a148d0099fe, fe50400a-7aae-40b4-865b-e9e0b3370195]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b85d74ba-41fa-4ec8-beb6-e0082fd1f197
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=661, sec_since_disconnect=7, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : fe50400a-7aae-40b4-865b-e9e0b3370195
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [196f6787-06ec-4c57-a05c-fb4d8123c6c7]
name                : eth21

_uuid               : 457aa162-ca34-44b2-af9d-baaab0b628f2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [651665c2-e4b7-43a2-9798-f0c515ca8bfe]
name                : eth23

_uuid               : 8da6292e-15c9-4159-a62d-7a148d0099fe
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [577daac0-d3ef-4547-bc80-7fcb41094939]
name                : eth22

_uuid               : 0280733f-d542-4220-8602-9e5706aea08a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [95895cfd-c434-4661-ac9d-c847f0f39b2f]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 577daac0-d3ef-4547-bc80-7fcb41094939
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1813179964, tx_dropped=0, tx_errors=0, tx_packets=47042248}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 95895cfd-c434-4661-ac9d-c847f0f39b2f
admin_state         : down
duplex              : full
ifindex             : 148
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

_uuid               : 651665c2-e4b7-43a2-9798-f0c515ca8bfe
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1762716704, tx_dropped=0, tx_errors=0, tx_packets=4038456}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 196f6787-06ec-4c57-a05c-fb4d8123c6c7
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
statistics          : {collisions=0, rx_bytes=3523529668, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=73977311, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1a9bb326d8411ec97adc0f34020efca09caf14c4
Author:     Ethan Jackson &lt;ethan@nicira.com&gt;
AuthorDate: Wed Sep 17 13:22:14 2014 -0700
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Wed Sep 17 18:24:52 2014 -0700

    ofproto: Warn about excessive rule counts in OpenFlow tables.
    
    Frequently we've run into controller bugs which result in hundreds of
    thousands, or even millions of rules being installed in an OpenFlow
    table.  This isn't something trouble-shooters naturally think of to
    check for, so it's nice to have a low rate warning message to hint at
    the potential problem.
    
    Signed-off-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
