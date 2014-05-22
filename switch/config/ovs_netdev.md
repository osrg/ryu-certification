---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1a85643c-02cd-4b3c-a833-e896584d9b3e
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f0060ada-ac2f-4c12-b864-62596c2f8484
controller          : [f902aaff-b646-4032-81ce-c710b96ae6ba]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [335f99f8-608c-4014-bc4e-aa4307edd993, 5c0f8e4f-263c-4037-a4b1-6849c2b3e219, 78ec45d3-7e9b-4268-9cec-8a2882a3dfc6, 9167ad81-4e17-43d1-bcbd-d83673d30dae]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f902aaff-b646-4032-81ce-c710b96ae6ba
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=552, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 335f99f8-608c-4014-bc4e-aa4307edd993
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [051105f6-82fa-470f-963d-a9a5a0d5977a]
name                : eth21

_uuid               : 9167ad81-4e17-43d1-bcbd-d83673d30dae
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [972a9474-d92d-41da-a0de-974dc9c4840b]
name                : br0

_uuid               : 78ec45d3-7e9b-4268-9cec-8a2882a3dfc6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e4c8c9c6-cb02-44ae-90a4-8cced8a3044b]
name                : eth23

_uuid               : 5c0f8e4f-263c-4037-a4b1-6849c2b3e219
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5401152c-d513-4338-8095-fb34acae507a]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 5401152c-d513-4338-8095-fb34acae507a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1725956708, tx_dropped=0, tx_errors=0, tx_packets=1155714}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 972a9474-d92d-41da-a0de-974dc9c4840b
admin_state         : down
duplex              : full
ifindex             : 151
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

_uuid               : 051105f6-82fa-470f-963d-a9a5a0d5977a
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
statistics          : {collisions=0, rx_bytes=4253929009, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2849441, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e4c8c9c6-cb02-44ae-90a4-8cced8a3044b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2971672500, tx_dropped=0, tx_errors=0, tx_packets=1981115}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9edf6b4828205610f7ea750bfb80fe960e1f01e3
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Wed May 21 20:45:24 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Wed May 21 20:48:01 2014 -0700

    ofproto-dpif-xlate: Fix a bug.
    
    Commit b256dc525c8 &#40;ofproto-dpif-xlate: Cache xlate_actions&#40;&#41; effects.&#41;
    caches the variables needed for refreshing mac-learning table in
    xlate_normal&#40;&#41;.  Wherein, the cache entry always records reference to
    the original 'ofproto'.
    
    When patch port is used to connect two 'ofproto's, packet goes through the
    patch port will have two mac-learning cache entries created for each
    'ofproto'.  So, each entry should reference to the corresponding 'ofproto'.
    However, due to the bug mentioned above, all cache entries will refer to the
    same 'ofproto'.  Subsequently, the mac-learning tables can be corrupted, which
    causes connection loss.
    
    This commit fixes the bug by making each cache entry refer to the correct
    'ofproto'.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
