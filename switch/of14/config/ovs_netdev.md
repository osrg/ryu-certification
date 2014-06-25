---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
885e6312-c8a2-42ca-a27a-77d1c0546aab
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 9f7af716-4af8-485f-9044-6f65ef289e98
controller          : [9c31679f-add0-4e55-b232-bb4f0c5895e0]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0e4d83d3-bc70-405b-aede-e410242d5e11, 485178e5-a686-457a-81d4-053da24c1f0f, 75bb1eb8-b090-48b0-9b9f-6995a341d065, 8e591f4c-6460-4b96-afc9-6f6214621fe6]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9c31679f-add0-4e55-b232-bb4f0c5895e0
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=976, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8e591f4c-6460-4b96-afc9-6f6214621fe6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [27d9cbba-5f99-4e2a-9953-af830b598a77]
name                : eth22

_uuid               : 75bb1eb8-b090-48b0-9b9f-6995a341d065
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b3ec5d33-238b-4b49-acc4-dde3a0ef34a3]
name                : br0

_uuid               : 485178e5-a686-457a-81d4-053da24c1f0f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9268b7a6-82f7-4bf8-912d-03ec471673ee]
name                : eth21

_uuid               : 0e4d83d3-bc70-405b-aede-e410242d5e11
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [23dedb67-f0e2-476c-988f-33443be19377]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 27d9cbba-5f99-4e2a-9953-af830b598a77
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2588186882, tx_dropped=0, tx_errors=0, tx_packets=36138594}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9268b7a6-82f7-4bf8-912d-03ec471673ee
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
statistics          : {collisions=0, rx_bytes=211871228, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=91906394, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 23dedb67-f0e2-476c-988f-33443be19377
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2411962284, tx_dropped=0, tx_errors=0, tx_packets=13061905}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b3ec5d33-238b-4b49-acc4-dde3a0ef34a3
admin_state         : down
duplex              : full
ifindex             : 710
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
commit 8bb113da32dd2aabcb958bb16941ba73ae4610b3
Author:     Ryan Wilson &lt;wryan@nicira.com&gt;
AuthorDate: Mon Jun 23 12:36:11 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jun 25 12:54:26 2014 -0700

    dpif-netdev: Implement batched flow dumping.
    
    Previously, flows were retrieved one by one when dumping flows for
    datapaths of type 'netdev'. This increased contention for the dump's
    mutex, negatively affecting revalidator performance.
    
    This patch retrieves batches of flows when dumping flows for datapaths
    of type 'netdev'.
    
    Signed-off-by: Ryan Wilson &lt;wryan@nicira.com&gt;
    [blp@nicira.com relaxed max_flows restriction]
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
