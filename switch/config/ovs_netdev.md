---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c7b215e3-2a76-4bd6-a93c-d7cab4ecf4ff
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 90dcf23a-8f8e-455f-9115-3950a0992cd8
controller          : [909b22aa-de16-41b1-869d-f7d9a244a77e]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [9ac1b98d-a998-44b5-9518-4733b2d59a3b, a50747b7-8369-4741-92a9-479ed11121af, c10cd367-39f4-4f3d-a284-60f95cdee2a3, ffd06a7d-0d62-4ac0-9c05-ec0525116655]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 909b22aa-de16-41b1-869d-f7d9a244a77e
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=967, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9ac1b98d-a998-44b5-9518-4733b2d59a3b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [891e2508-fb1a-49ae-89b3-b0892f18090e]
name                : br0

_uuid               : ffd06a7d-0d62-4ac0-9c05-ec0525116655
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0f032116-2b50-40f1-b5a4-b64a4e0c73f9]
name                : eth22

_uuid               : c10cd367-39f4-4f3d-a284-60f95cdee2a3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1c100b24-814d-477c-8df8-64da3d0a3118]
name                : eth23

_uuid               : a50747b7-8369-4741-92a9-479ed11121af
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [88548a03-aaee-45d7-875d-f5a9e2bd2be9]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1c100b24-814d-477c-8df8-64da3d0a3118
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3300938204, tx_dropped=0, tx_errors=0, tx_packets=5063937}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 891e2508-fb1a-49ae-89b3-b0892f18090e
admin_state         : down
duplex              : full
ifindex             : 334
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

_uuid               : 0f032116-2b50-40f1-b5a4-b64a4e0c73f9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2516580662, tx_dropped=0, tx_errors=0, tx_packets=4556992}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 88548a03-aaee-45d7-875d-f5a9e2bd2be9
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
statistics          : {collisions=0, rx_bytes=2814711173, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=10511337, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit b0e2ec321f384fb2ea4300529717a5cc09e0c096
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Mon Jun 2 14:02:19 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Mon Jun 2 14:02:19 2014 -0700

    lib/flow: fix minimatch_extract&#40;&#41; ICMPv6 parsing
    
    This patch addresses two bugs related to ICMPv6&#40;NDP&#41; packets:
    
    - In miniflow_extract&#40;&#41; push the words in the correct order
    - In parse_icmpv6&#40;&#41; use sizeof struct, not size of struct *
    
    match_wc_init&#40;&#41; has been modified, to include the nd_target field
    when the transport layer protocol is ICMPv6
    
    A testcase has been added to detect the bugs.
    
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
