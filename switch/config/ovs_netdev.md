---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
baf50411-2fe9-4cad-a7c8-0919e7d8ffd0
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
_uuid               : a44c2a61-f3e1-4a48-85c8-54d661c5d7a4
controller          : [abc2d574-f07d-4501-b08a-b9976d32072f]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [33e1d690-bba6-4de8-825b-5aa38f7871e2, a692aa7e-e329-4924-aec1-de17b7573e49, f24a2cd4-e08f-4bb7-87af-518196714633]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : abc2d574-f07d-4501-b08a-b9976d32072f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=377, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f24a2cd4-e08f-4bb7-87af-518196714633
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3f285b4f-1e23-4a7e-9d49-05728b99de8e]
name                : br0

_uuid               : 33e1d690-bba6-4de8-825b-5aa38f7871e2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8ebd789b-51dc-428d-9a48-504dd0c8c3f5]
name                : eth7

_uuid               : a692aa7e-e329-4924-aec1-de17b7573e49
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bf676419-0409-4c1d-8809-4776a1fa8d38]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : bf676419-0409-4c1d-8809-4776a1fa8d38
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3375626, tx_dropped=0, tx_errors=0, tx_packets=36019}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 3f285b4f-1e23-4a7e-9d49-05728b99de8e
admin_state         : up
duplex              : full
ifindex             : 466
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

_uuid               : 8ebd789b-51dc-428d-9a48-504dd0c8c3f5
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
statistics          : {collisions=0, rx_bytes=3062123840, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72623694, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 619d5f98e1fe5fb08929086cca97fb7d51a3fe84
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Thu Mar 6 17:20:27 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Mar 11 16:04:13 2014 -0700

    tests: Test learned flow idle timeouts.
    
    The previous tests would check that a single learned flow had its stats
    correctly attributed to the right interfaces and flows. These new tests
    take it a step further by causing two different learned flows to be
    created, and checking the stats are correct. This is done for rules that
    are learned with idle and hard timeouts.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
