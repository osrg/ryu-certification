---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
71158af9-d5dc-4ad0-aa5d-5e8bc78384bc
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c3436ed4-2351-45bc-8070-2721e27f6b7d
controller          : [bbd60a53-5187-4b80-8945-b4bd7cd3e5ff]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0ac37b50-a292-4b08-a1d5-df9817444ff1, 65a9295c-70b5-48be-a472-6f2b16470c04, 90aea10b-00da-4ad2-a1ee-f9ac9d575bf5, bb60fde4-bf06-41d7-a4d8-179afcf990b6]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : bbd60a53-5187-4b80-8945-b4bd7cd3e5ff
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=967, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0ac37b50-a292-4b08-a1d5-df9817444ff1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [32ff6fef-3876-4ee0-9e7a-893da602eac3]
name                : eth21

_uuid               : bb60fde4-bf06-41d7-a4d8-179afcf990b6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6b741d61-4daf-40be-bf28-d109f0d73187]
name                : br0

_uuid               : 65a9295c-70b5-48be-a472-6f2b16470c04
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [df0a735e-59a4-4e56-9a0e-b0f2437cbae7]
name                : eth22

_uuid               : 90aea10b-00da-4ad2-a1ee-f9ac9d575bf5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9f7242cd-bc77-4be9-8d58-23ef496bdc82]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6b741d61-4daf-40be-bf28-d109f0d73187
admin_state         : down
duplex              : full
ifindex             : 529
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

_uuid               : 9f7242cd-bc77-4be9-8d58-23ef496bdc82
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4206455876, tx_dropped=0, tx_errors=0, tx_packets=8531611}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : df0a735e-59a4-4e56-9a0e-b0f2437cbae7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2879588965, tx_dropped=0, tx_errors=0, tx_packets=13406601}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 32ff6fef-3876-4ee0-9e7a-893da602eac3
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
statistics          : {collisions=0, rx_bytes=4184529072, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28646088, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit cccc12cc3a6ae94b9cce89802fe68bc8d03f28b8
Author:     Thomas Graf &lt;tgraf@noironetworks.com&gt;
AuthorDate: Tue Jun 17 22:58:02 2014 +0000
Commit:     Justin Pettit &lt;jpettit@nicira.com&gt;
CommitDate: Tue Jun 17 09:15:47 2014 -0700

    ovs-vsctl: Fix OF protocol name capitalization in manual page
    
    Signed-off-by: Thomas Graf &lt;tgraf@noironetworks.com&gt;
    Signed-off-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
