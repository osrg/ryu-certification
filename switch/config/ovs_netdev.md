---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
266937a6-6004-4c33-baf5-387f07b1920a
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 76253a10-4eac-4b97-ada9-d5c2c1a1e998
controller          : [a74336c0-5279-4cbd-9b9f-bde6ee2dfe8e]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [14ee6538-f5b4-4e31-af43-dd12e6b30ab0, 6801a2e6-36f6-4746-8d87-256beb07b503, a558ccad-6248-4f5d-8deb-5c87b86f15de, dc336646-4eaf-4c35-a563-065eff7582af]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a74336c0-5279-4cbd-9b9f-bde6ee2dfe8e
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=666, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 14ee6538-f5b4-4e31-af43-dd12e6b30ab0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c8ae28bc-3abe-45a4-b7c2-ba673719c792]
name                : eth22

_uuid               : a558ccad-6248-4f5d-8deb-5c87b86f15de
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e3e822a6-4a0d-47db-9858-1fece893514f]
name                : br0

_uuid               : dc336646-4eaf-4c35-a563-065eff7582af
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [749e11e7-a02f-48aa-bd84-7094f3348f19]
name                : eth23

_uuid               : 6801a2e6-36f6-4746-8d87-256beb07b503
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [99e10e56-8429-47a2-b801-a7a1029ec020]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c8ae28bc-3abe-45a4-b7c2-ba673719c792
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2234458290, tx_dropped=0, tx_errors=0, tx_packets=47325449}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e3e822a6-4a0d-47db-9858-1fece893514f
admin_state         : down
duplex              : full
ifindex             : 164
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

_uuid               : 99e10e56-8429-47a2-b801-a7a1029ec020
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
statistics          : {collisions=0, rx_bytes=163648849, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=74605760, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 749e11e7-a02f-48aa-bd84-7094f3348f19
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2463431204, tx_dropped=0, tx_errors=0, tx_packets=4505599}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 13a30965fad9df08125bbbce0b2958309f64146e
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Sun Sep 21 11:41:28 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Sun Sep 21 11:52:10 2014 -0700

    datapath: compat: Fix compilation for 2.6.32 kernel
    
    Define alloc_netdev&#40;&#41; using alloc_netdev_mq&#40;&#41; which is available on all
    kernel supported by OVS.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
