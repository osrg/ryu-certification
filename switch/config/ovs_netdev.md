---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d4ae7c5e-8baf-45f7-a748-24ebca0546f4
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
_uuid               : fc197bde-18b5-45ae-93ef-b1b1f74d5d03
controller          : [68c7f63f-cfd1-43c6-a4e4-998495318df5]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [15d97b80-927b-4e42-be65-89d50227ca0a, 8979093e-2fbb-4fe7-8296-104afc38230d, fa070c56-7c98-48e6-a353-a793866ff495]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 68c7f63f-cfd1-43c6-a4e4-998495318df5
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=556, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 15d97b80-927b-4e42-be65-89d50227ca0a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2862a6f4-7eff-4012-b858-b4b069448752]
name                : eth7

_uuid               : 8979093e-2fbb-4fe7-8296-104afc38230d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dd3effa1-25fa-4758-9209-75e749ab2581]
name                : br0

_uuid               : fa070c56-7c98-48e6-a353-a793866ff495
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6b59f232-b9a5-4fb0-83b6-b0007db344f2]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2862a6f4-7eff-4012-b858-b4b069448752
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
statistics          : {collisions=0, rx_bytes=3076333098, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72768298, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : dd3effa1-25fa-4758-9209-75e749ab2581
admin_state         : down
duplex              : full
ifindex             : 1018
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 6b59f232-b9a5-4fb0-83b6-b0007db344f2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7630045, tx_dropped=0, tx_errors=0, tx_packets=81335}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 62c70c9d47edf2dbf5c9d0c8cd6c15c8c43dc7a8
Merge: 7942825 698ffe3
Author:     ejj &lt;ethan@nicira.com&gt;
AuthorDate: Thu Apr 17 17:35:52 2014 -0700
Commit:     ejj &lt;ethan@nicira.com&gt;
CommitDate: Thu Apr 17 17:35:52 2014 -0700

    Merge pull request #3 from joestringer/submit/xlate_cache_v2
    
    Cache the modules affected by xlate_actions().
</pre>
