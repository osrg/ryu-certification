---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
bc5cc348-eeb8-4fce-83f8-55afaddc0aa4
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : acc665d5-bcc0-4920-bb8d-497e0b4d7dbd
controller          : [ff3566c0-06c0-43c8-9999-7f9107d15e2e]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [21e48004-c834-43ec-a3bf-d6eec2ad1d5d, 73ce566d-5fef-4220-9c86-3650b323b906, 8370d652-8c2a-4982-b1ea-34b67fe0a3f7, bce3b456-42ed-4248-8bd6-0c81a252b176]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ff3566c0-06c0-43c8-9999-7f9107d15e2e
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=756, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 21e48004-c834-43ec-a3bf-d6eec2ad1d5d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1bc99c0b-4a26-4104-88ee-3b133f376f3b]
name                : eth21

_uuid               : 73ce566d-5fef-4220-9c86-3650b323b906
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9f7fd9ea-8983-4f63-a3df-2b00a3498b01]
name                : eth23

_uuid               : bce3b456-42ed-4248-8bd6-0c81a252b176
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2d0be428-c041-47fa-a757-8dad6d2a7ab1]
name                : eth22

_uuid               : 8370d652-8c2a-4982-b1ea-34b67fe0a3f7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cc6f343c-ebce-4e03-b67d-93d10c1e3c11]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2d0be428-c041-47fa-a757-8dad6d2a7ab1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1865962124, tx_dropped=0, tx_errors=0, tx_packets=47077729}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : cc6f343c-ebce-4e03-b67d-93d10c1e3c11
admin_state         : down
duplex              : full
ifindex             : 150
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

_uuid               : 9f7fd9ea-8983-4f63-a3df-2b00a3498b01
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1850192204, tx_dropped=0, tx_errors=0, tx_packets=4096773}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 1bc99c0b-4a26-4104-88ee-3b133f376f3b
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
statistics          : {collisions=0, rx_bytes=3640427376, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=74055874, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
