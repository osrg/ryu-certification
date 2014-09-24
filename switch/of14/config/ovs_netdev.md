---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
91151a5b-1af9-4e58-a7b5-a832c787d971
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f97efc35-25b5-4957-ac43-e4a306dac030
controller          : [07d07d5e-c8f5-4cf3-9cde-53797c3ad2f3]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [960b03cf-80fd-42b8-b203-bfcad4b2cac7, cb05947f-bbe6-41ef-947a-f2b02027d413, e5135a76-f2ce-4682-bc7d-8b99faa936f4, fc05e8f2-f771-4d59-848a-82ebac83c6ce]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 07d07d5e-c8f5-4cf3-9cde-53797c3ad2f3
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=667, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e5135a76-f2ce-4682-bc7d-8b99faa936f4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ddad4043-a2f9-4e88-838a-8c889e7326d3]
name                : br0

_uuid               : fc05e8f2-f771-4d59-848a-82ebac83c6ce
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c87632a4-15a6-4892-9008-2e3a34d73bb4]
name                : eth23

_uuid               : 960b03cf-80fd-42b8-b203-bfcad4b2cac7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4de2a21b-c74d-445e-9ced-3fe883d4dcde]
name                : eth21

_uuid               : cb05947f-bbe6-41ef-947a-f2b02027d413
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [519851b8-6b44-4575-a4cc-2e9a879d1fb8]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 519851b8-6b44-4575-a4cc-2e9a879d1fb8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2507425656, tx_dropped=0, tx_errors=0, tx_packets=47508792}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c87632a4-15a6-4892-9008-2e3a34d73bb4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2877701204, tx_dropped=0, tx_errors=0, tx_packets=4781779}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ddad4043-a2f9-4e88-838a-8c889e7326d3
admin_state         : down
duplex              : full
ifindex             : 173
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

_uuid               : 4de2a21b-c74d-445e-9ced-3fe883d4dcde
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
statistics          : {collisions=0, rx_bytes=736402811, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=74990521, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6db454dc00fa5d9693ebdf6c5e10c61030f8df8e
Author:     Simon Horman &lt;simon.horman@netronome.com&gt;
AuthorDate: Wed Sep 24 12:41:02 2014 +0000
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Wed Sep 24 14:00:15 2014 -0700

    ofproto-dpif-rid: correct logic error in rid_pool_alloc_id&#40;&#41;
    
    When searching through the valid ids an id should
    be used if is not found rather than if it is found.
    
    It appears to me that without this change duplicate recirculation
    ids may used in cases where the last recirculation id has
    been allocated; selection loops back to the beginning of the pool and;
    reaches a recirculation id that is still in use.
    
    As the number of recirculation ids is currently RECIRC_ID_N_IDS = 1024 this
    does not seem beyond the bounds of possibility.
    
    I have not verified that such a scenario can actually occur.  But it seems
    that a likely consequence would be that some packets may be forwarded
    incorrectly.
    
    Signed-off-by: Simon Horman &lt;simon.horman@netronome.com&gt;
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
