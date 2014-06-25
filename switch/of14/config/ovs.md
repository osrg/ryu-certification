---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c055c829-0b3a-4568-8948-10177504b657
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 936613f2-8e57-46dc-b37f-59026c470927
controller          : [25915048-fc14-4989-8564-09195a450f80]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [484463e3-e92b-4af3-a6b6-264b0dad8b34, bc50c8f4-8cb2-4e8a-b601-0f335e554e21, dc193b65-08fb-47bb-83be-c49e62f06822, e4acbc30-9242-431d-b20a-e76b957f6196]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 25915048-fc14-4989-8564-09195a450f80
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=647, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : bc50c8f4-8cb2-4e8a-b601-0f335e554e21
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4975c255-b6e3-45d4-af63-b36272ed3fd2]
name                : eth23

_uuid               : e4acbc30-9242-431d-b20a-e76b957f6196
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [00015b67-1bd8-4460-9d40-cde96b962e4f]
name                : eth22

_uuid               : dc193b65-08fb-47bb-83be-c49e62f06822
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [48c3031d-2749-4d57-be4c-739e5c5796f2]
name                : eth21

_uuid               : 484463e3-e92b-4af3-a6b6-264b0dad8b34
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9a78d5ba-8af9-451e-a962-5a9014edc271]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4975c255-b6e3-45d4-af63-b36272ed3fd2
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=3057008784, tx_dropped=0, tx_errors=0, tx_packets=13491936}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 48c3031d-2749-4d57-be4c-739e5c5796f2
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
statistics          : {collisions=0, rx_bytes=1018409590, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=92448270, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9a78d5ba-8af9-451e-a962-5a9014edc271
admin_state         : down
ifindex             : 723
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

_uuid               : 00015b67-1bd8-4460-9d40-cde96b962e4f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2889822952, tx_dropped=0, tx_errors=0, tx_packets=36341513}
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
