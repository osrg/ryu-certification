---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9d9b7e12-ee71-40e6-8317-3d3ac58a3657
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7a865dfa-4cbc-4b57-a032-38869bb747d5
controller          : [3fd97096-a090-4ce3-9797-153f707905cf]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [41761728-4c80-4217-bfbf-c5fb5476ca57, 4f276982-e6c0-425a-9df7-e6bcda41c34a, a7c7d234-9c43-4df1-83f5-12265c9a3e2f, cba4a04d-584e-4249-b28b-35cd7c02325e]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3fd97096-a090-4ce3-9797-153f707905cf
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=662, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 41761728-4c80-4217-bfbf-c5fb5476ca57
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6ada0d29-f7ee-4d41-adaa-78a29e1f385c]
name                : eth22

_uuid               : a7c7d234-9c43-4df1-83f5-12265c9a3e2f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fa6f39a9-dc04-494a-9035-cbc40ee6c844]
name                : eth21

_uuid               : cba4a04d-584e-4249-b28b-35cd7c02325e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c18dc4cc-f69d-42fb-adc1-1f97c37f96b4]
name                : eth23

_uuid               : 4f276982-e6c0-425a-9df7-e6bcda41c34a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [487c0d9b-0999-48ed-b9a3-63c7baaf309e]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c18dc4cc-f69d-42fb-adc1-1f97c37f96b4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2697121500, tx_dropped=0, tx_errors=0, tx_packets=1798081}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6ada0d29-f7ee-4d41-adaa-78a29e1f385c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1229763420, tx_dropped=0, tx_errors=0, tx_packets=49508558}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : fa6f39a9-dc04-494a-9035-cbc40ee6c844
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
statistics          : {collisions=0, rx_bytes=2074011703, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=84447177, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 487c0d9b-0999-48ed-b9a3-63c7baaf309e
admin_state         : down
ifindex             : 77
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fb42720ed20a4268d44df3f39e3ec5fd00261e28
Author:     Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
AuthorDate: Thu Aug 7 01:35:11 2014 +0000
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Wed Aug 6 10:58:22 2014 -0700

    test-atomic: Fix warnings for GCC4.9 and sparse
    
    There's no reason for the local variable 'old_count' to be atomic. In fact, if
    it is atomic it triggers a GCC4.9 warning &#40;Wunused-value&#41;
    The global variables 'a' and 'paux' could be static, according to sparse.
    
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
