---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
997ed716-661f-4ee4-b1b1-570a69e586bb
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8919f10e-ce80-42f8-8154-638812b14ba0
controller          : [23b6e007-9c6c-46aa-869a-dc2752d54342]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [931e96a2-e00f-4274-b426-aed54681d7e4, 952eeebd-97b9-4f57-bb99-f6b642bb554e, ea4dc534-af0c-403b-83db-f695ff384ceb]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 23b6e007-9c6c-46aa-869a-dc2752d54342
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=382, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ea4dc534-af0c-403b-83db-f695ff384ceb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [68bf6035-3ed6-4230-bc92-af3cc2a6beff]
name                : eth7

_uuid               : 952eeebd-97b9-4f57-bb99-f6b642bb554e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ad84645d-a06f-4872-8140-f04e5da117a0]
name                : br0

_uuid               : 931e96a2-e00f-4274-b426-aed54681d7e4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [26b00b4a-1b56-438c-afb9-bb9715382b83]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ad84645d-a06f-4872-8140-f04e5da117a0
admin_state         : up
duplex              : full
ifindex             : 654
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

_uuid               : 68bf6035-3ed6-4230-bc92-af3cc2a6beff
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
statistics          : {collisions=0, rx_bytes=3067082288, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72673989, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 26b00b4a-1b56-438c-afb9-bb9715382b83
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4836952, tx_dropped=0, tx_errors=0, tx_packets=51576}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5bb8a63029eb594e208ed31e8f5d6351375c19da
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Wed Mar 19 16:19:44 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Thu Mar 20 10:49:25 2014 -0700

    cfm: Add test for the update of CFM status to OVSDB.
    
    Since daemons can use the cfm status from OVSDB, it is useful
    to add a test to guarantee that the update is in time.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
