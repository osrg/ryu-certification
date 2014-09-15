---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
014d9af9-0615-498d-856f-76788501cd6b
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e9c808c5-2d41-4557-9ce5-bfbbb14de06d
controller          : [e7436265-c39b-4133-9190-676d0991c910]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2cca58c4-b842-4e9b-9544-bfca02842af2, 30a8ba96-f60d-4889-9ffe-5230a7e6ad8a, 438c9318-e528-4521-b46a-2758c6732027, f5ffd790-7435-46a3-90ce-05c2eff5b044]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e7436265-c39b-4133-9190-676d0991c910
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=696, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2cca58c4-b842-4e9b-9544-bfca02842af2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [06bdc259-0c5f-4f6d-9d2d-011c18a078ba]
name                : br0

_uuid               : 438c9318-e528-4521-b46a-2758c6732027
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bcee7eaa-08bd-4de5-9fac-30f156be90c5]
name                : eth23

_uuid               : f5ffd790-7435-46a3-90ce-05c2eff5b044
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [76c16216-712c-4c2b-b14e-393f3155c52e]
name                : eth22

_uuid               : 30a8ba96-f60d-4889-9ffe-5230a7e6ad8a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e73cb3ec-9c6f-42f0-beaa-6f2268cfe2b9]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e73cb3ec-9c6f-42f0-beaa-6f2268cfe2b9
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
statistics          : {collisions=0, rx_bytes=3248739662, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=65198993, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 06bdc259-0c5f-4f6d-9d2d-011c18a078ba
admin_state         : down
duplex              : full
ifindex             : 136
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

_uuid               : 76c16216-712c-4c2b-b14e-393f3155c52e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3645297984, tx_dropped=0, tx_errors=0, tx_packets=45398139}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : bcee7eaa-08bd-4de5-9fac-30f156be90c5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1190018204, tx_dropped=0, tx_errors=0, tx_packets=3656657}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 2f9dd77fcd172e2870d737ede67970836db3eb14
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Fri Sep 12 16:00:50 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Mon Sep 15 10:08:56 2014 -0700

    ofproto: Do not update stats on fake bond interface.
    
    There are couple of reasons to remove this support:
    *   This is used in very old OVS use-case. It is much better
        to read stats directly from OVS.
    *   Forthcoming commit will remove support for setting stats
        for vport. The stats update depends on stats-set.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
