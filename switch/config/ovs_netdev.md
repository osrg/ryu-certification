---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0e642f06-d8dd-40ad-98bd-d547582b396b
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 912e19df-7f96-4bbd-a318-d174a2739560
controller          : [f30dfbe9-a077-4295-b159-fd7295c49042]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0efce2bf-cf3c-4333-8ee4-f0f1cd9940e1, 757ecde4-494b-4d9f-bb6c-801ceb98e218, be352194-8078-4e8a-9880-393adf22f6a6, c154caee-7d4e-4399-9b81-2dd7a5726241]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f30dfbe9-a077-4295-b159-fd7295c49042
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=557, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : be352194-8078-4e8a-9880-393adf22f6a6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [118d2b18-89ae-4e06-9d43-cd0c17d9b679]
name                : eth21

_uuid               : 757ecde4-494b-4d9f-bb6c-801ceb98e218
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [33143d7d-d268-48b3-8da2-094202967699]
name                : eth23

_uuid               : c154caee-7d4e-4399-9b81-2dd7a5726241
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e27114a0-ff06-4f5b-ac73-7f6721f6b66e]
name                : br0

_uuid               : 0efce2bf-cf3c-4333-8ee4-f0f1cd9940e1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [80859270-c32e-4348-9cee-8c1c8ede01e2]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 118d2b18-89ae-4e06-9d43-cd0c17d9b679
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
statistics          : {collisions=0, rx_bytes=1309086962, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=877111, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e27114a0-ff06-4f5b-ac73-7f6721f6b66e
admin_state         : down
duplex              : full
ifindex             : 69
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

_uuid               : 80859270-c32e-4348-9cee-8c1c8ede01e2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=449395894, tx_dropped=0, tx_errors=0, tx_packets=301187}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 33143d7d-d268-48b3-8da2-094202967699
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1023189000, tx_dropped=0, tx_errors=0, tx_packets=682126}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5a87054c2d832d0e10b30a1f223707acb8efbeb7
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Mon May 19 10:41:03 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Mon May 19 10:41:03 2014 -0700

    lib/classifier: Rename 'cls_subtable_cache' as 'cls_subtables'.
    
    'cache' gives an inexact connotation, as the list is always expected
    to be in order and contain pointers to all the subtables.
    
    The struct cls_subtables fields are are also renamed to be more readable.
    
    struct cls_classifier fields 'subtables' is remamed to 'subtables_map' and
    'subtables_priority' is renamed to 'subtables',
    
    There are no functional changes in this patch.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
