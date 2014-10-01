---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8c9aa472-028c-4b5c-98e3-e34da591e151
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0d2f93b3-78e1-4fb5-bd0a-6b885e7ec68d
controller          : [be417303-5486-46e1-8c8a-6bddfe0caff1]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [44885dc8-2d5b-41e6-81c0-ec67ac497089, 7b0bab66-6f9d-42fa-a86c-dbcee11a45e7, 80ad236f-c2be-4aff-96ea-56ba220adcdc, f515f2c2-797b-4b87-911d-3e75f6fa2072]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : be417303-5486-46e1-8c8a-6bddfe0caff1
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=667, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 44885dc8-2d5b-41e6-81c0-ec67ac497089
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [73b637cc-43cf-4b51-aaf8-95a180f92c57]
name                : eth23

_uuid               : 7b0bab66-6f9d-42fa-a86c-dbcee11a45e7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [47522e5b-6dd0-46c9-b460-55076d9f7a8b]
name                : eth21

_uuid               : f515f2c2-797b-4b87-911d-3e75f6fa2072
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [af53e60e-9e4b-4a09-84dc-e1fb7e943618]
name                : br0

_uuid               : 80ad236f-c2be-4aff-96ea-56ba220adcdc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4feee925-5bd1-4d9c-aac7-622ffb0421eb]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 73b637cc-43cf-4b51-aaf8-95a180f92c57
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3816497204, tx_dropped=0, tx_errors=0, tx_packets=5407643}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 4feee925-5bd1-4d9c-aac7-622ffb0421eb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3097559982, tx_dropped=0, tx_errors=0, tx_packets=47905337}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : af53e60e-9e4b-4a09-84dc-e1fb7e943618
admin_state         : down
duplex              : full
ifindex             : 194
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

_uuid               : 47522e5b-6dd0-46c9-b460-55076d9f7a8b
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
statistics          : {collisions=0, rx_bytes=2010652521, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=75846733, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7530fe0d8a69b0f9477f94f9883e9e31ad3630b1
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Wed Oct 1 11:49:10 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Wed Oct 1 13:02:50 2014 -0700

    cmap: ovsrcu postpone the cmap destroy.
    
    Currently, the cmap_destroy&#40;&#41; directly frees the cmap memory.
    Some callers of cmap_destroy&#40;&#41; &#40;e.g. destroy_subtable&#40;&#41;&#41; still
    allows other threads &#40;e.g. pmd threads&#41; accessing the cmap at
    the same time &#40;e.g. via classifier_lookup_miniflow_batch&#40;&#41;&#41;,
    which could cause segfault.
    
    To fix the above issue, this commit use ovsrcu to postpone
    the free of cmap memory.
    
    Reported-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
