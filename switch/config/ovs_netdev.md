---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b3ad93ba-0d7b-482f-aa41-76bfcc2b9475
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7779db7b-e8d6-4e0d-bf05-e8301c04195e
controller          : [9cabd6f6-bc78-41e7-83ab-8ed7d5dd7710]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [8b9a289e-51ee-4df4-9cf9-887a40b78f0a, 9c29c6ad-702b-4835-93ac-4d58073e544e, c4b7a37f-2441-4d00-811b-ba581740e389, ff0b3536-790c-4dd6-8557-130f49ed18bf]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9cabd6f6-bc78-41e7-83ab-8ed7d5dd7710
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=551, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9c29c6ad-702b-4835-93ac-4d58073e544e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f5bb4905-f624-4914-92af-5704a9183d49]
name                : eth21

_uuid               : ff0b3536-790c-4dd6-8557-130f49ed18bf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a9970244-aa8c-421b-af92-8e6b16f36315]
name                : eth23

_uuid               : 8b9a289e-51ee-4df4-9cf9-887a40b78f0a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [21ee1584-8287-4f2d-bf5c-a59bce2c1944]
name                : br0

_uuid               : c4b7a37f-2441-4d00-811b-ba581740e389
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cd41417b-f301-443f-8a4e-78bcb190dda8]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 21ee1584-8287-4f2d-bf5c-a59bce2c1944
admin_state         : down
duplex              : full
ifindex             : 176
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

_uuid               : a9970244-aa8c-421b-af92-8e6b16f36315
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2100856500, tx_dropped=0, tx_errors=0, tx_packets=1400571}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f5bb4905-f624-4914-92af-5704a9183d49
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
statistics          : {collisions=0, rx_bytes=3141287457, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2108778, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : cd41417b-f301-443f-8a4e-78bcb190dda8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1312692026, tx_dropped=0, tx_errors=0, tx_packets=880512}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 8c1b077f62126633ac67b5babf0cfc6147f3a167
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Tue May 13 10:07:18 2014 +1200
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Thu May 15 10:20:23 2014 +1200

    odp-util: Fix a comment.
    
    The comment was very specific to one user of the function, and had a
    typo. This change reflects the wider effect of the case.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
