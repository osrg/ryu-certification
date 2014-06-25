---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
bb57d959-7a24-4d29-800c-85df59ff0fac
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
_uuid               : 0c23eae8-7d4a-4d4e-89d3-ee4f90897f1e
controller          : [e4ccb1cd-4b08-4f06-96ff-dc2621c3ab84]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1ce6ea52-5fba-4cd7-8bae-7e5561aea6fa, a7a2f145-e209-4805-9908-b9e9e2fab765, d77a1aea-ea39-4856-9365-02d1e3e620be, f3a6d303-1d64-4682-96db-5d05f88579f7]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e4ccb1cd-4b08-4f06-96ff-dc2621c3ab84
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=647, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a7a2f145-e209-4805-9908-b9e9e2fab765
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f5960c6e-5a84-48d8-aad8-021fb93eba60]
name                : eth22

_uuid               : d77a1aea-ea39-4856-9365-02d1e3e620be
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8335af15-c0a3-4f83-a1d5-80cff6c45922]
name                : eth23

_uuid               : 1ce6ea52-5fba-4cd7-8bae-7e5561aea6fa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [029991e6-4c59-4c7f-a2ff-0b5b52c033b2]
name                : eth21

_uuid               : f3a6d303-1d64-4682-96db-5d05f88579f7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [91cbe2ac-6aee-44a5-9fb7-2990d2359189]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 91cbe2ac-6aee-44a5-9fb7-2990d2359189
admin_state         : down
duplex              : full
ifindex             : 719
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

_uuid               : 8335af15-c0a3-4f83-a1d5-80cff6c45922
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2858467284, tx_dropped=0, tx_errors=0, tx_packets=13359575}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f5960c6e-5a84-48d8-aad8-021fb93eba60
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2807858132, tx_dropped=0, tx_errors=0, tx_packets=36286284}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 029991e6-4c59-4c7f-a2ff-0b5b52c033b2
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
statistics          : {collisions=0, rx_bytes=784633598, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=92291158, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 26a5075bb6a0c96a94ea5be7672185a2a8f3eedc
Author:     Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
AuthorDate: Wed Jun 25 11:39:34 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Wed Jun 25 14:35:50 2014 -0700

    dpif-netdev: delete lost packets in dp_execute_cb&#40;&#41;
    
    This commit fixes memory leaks in dp_execute_cb&#40;&#41; in two cases:
        - when the output port cannot be found
        - when the recirculation depth is exceeded
    
    Reported-by: Pravin Shelar &lt;pshelar@nicira.com&gt;
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
