---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f60774e0-2290-4395-b9f9-eba241ed9526
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c202f0e1-40e4-4f4a-abed-f4c7bad03124
controller          : [17c0b453-df3b-4d50-aed7-615d6cf7d610]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [23fadf90-a275-4f9b-83cf-0ea4cce90189, 43d3f15d-7b2e-48f1-8572-cccd0a0c87d8, 93f6c0d5-03eb-49e0-90e2-f5c36aa83bcb]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 17c0b453-df3b-4d50-aed7-615d6cf7d610
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=316, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 23fadf90-a275-4f9b-83cf-0ea4cce90189
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c6f98427-be76-4bda-bfc0-4d505f54c26a]
name                : eth7

_uuid               : 43d3f15d-7b2e-48f1-8572-cccd0a0c87d8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2860e117-b275-4193-ba11-65526f5bb8b0]
name                : eth8

_uuid               : 93f6c0d5-03eb-49e0-90e2-f5c36aa83bcb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3970edf5-3000-4124-a80a-c40551356476]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3970edf5-3000-4124-a80a-c40551356476
admin_state         : up
duplex              : full
ifindex             : 801
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

_uuid               : 2860e117-b275-4193-ba11-65526f5bb8b0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6133671, tx_dropped=0, tx_errors=0, tx_packets=65384}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : c6f98427-be76-4bda-bfc0-4d505f54c26a
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
statistics          : {collisions=0, rx_bytes=3071469623, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72718514, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0641a4fbd74d47648ae79208ab36ae3d35284a4d
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Sat Mar 29 15:52:32 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Sat Mar 29 15:52:32 2014 -0700

    datapath: Make flow mask removal symmetric.
    
    Masks are inserted when flows are inserted to the table, so it is
    logical to correspondingly remove masks when flows are removed from
    the table, in ovs_flow_table_remove().
    
    This allows ovs_flow_free() to be called without locking, which will
    be used by later patches.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;Summary:
</pre>
