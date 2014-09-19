---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
47e9922b-7f18-4ee6-ac54-dd189a6dc137
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : fed635f3-8d14-4ea8-8e68-d6d2fdb3294e
controller          : [60af1456-d767-40a8-9107-033e45b978b2]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [41384266-0df7-486e-b1f6-86a1883b4df2, a219dde5-2cde-4920-974b-c7d48e654d21, ee0819d8-d0ea-4605-9972-d568fd8c2724, fdbaaeb6-9f12-4654-bd9a-2a0b4cc870a0]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 60af1456-d767-40a8-9107-033e45b978b2
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=666, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ee0819d8-d0ea-4605-9972-d568fd8c2724
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7c2c625b-2119-4669-8318-b7a2a7ce09ce]
name                : eth22

_uuid               : a219dde5-2cde-4920-974b-c7d48e654d21
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0557e19c-5398-49c8-bd6e-f25156fa4911]
name                : br0

_uuid               : 41384266-0df7-486e-b1f6-86a1883b4df2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8503bc8e-9610-45b5-bac0-4cfc8a376959]
name                : eth21

_uuid               : fdbaaeb6-9f12-4654-bd9a-2a0b4cc870a0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8c36611e-d548-43be-9b28-3fb8b85e0581]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0557e19c-5398-49c8-bd6e-f25156fa4911
admin_state         : down
duplex              : full
ifindex             : 152
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

_uuid               : 8503bc8e-9610-45b5-bac0-4cfc8a376959
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
statistics          : {collisions=0, rx_bytes=3757292897, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=74134424, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8c36611e-d548-43be-9b28-3fb8b85e0581
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1937630204, tx_dropped=0, tx_errors=0, tx_packets=4155065}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 7c2c625b-2119-4669-8318-b7a2a7ce09ce
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1918749330, tx_dropped=0, tx_errors=0, tx_packets=47113219}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 8827798536e4d6076572558b46661c0a70ff432b
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Sep 19 08:24:11 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Sep 19 10:26:14 2014 -0700

    coverage: Remove unused macro.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
