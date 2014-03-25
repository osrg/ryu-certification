---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
be1a029b-115a-4436-b235-76feb4a86ab1
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : af42cf8a-81b6-4a0a-bf08-fbbc75e8fd07
controller          : [2d39c29e-290e-4118-8baf-ed14379fcb25]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [497764b8-ade5-4f84-bb49-ec82da949012, a14c3616-6c6c-4123-aeee-a34d172e3915, f1c04d4b-156f-4ac7-9344-4c7c863f9c50]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2d39c29e-290e-4118-8baf-ed14379fcb25
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=376, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 497764b8-ade5-4f84-bb49-ec82da949012
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f9ce74b9-4105-4f37-9515-e7d2e75649cf]
name                : eth8

_uuid               : a14c3616-6c6c-4123-aeee-a34d172e3915
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7d020da8-109b-4ab6-95f4-7dfcef7b5119]
name                : eth7

_uuid               : f1c04d4b-156f-4ac7-9344-4c7c863f9c50
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [94bdaa0b-65aa-40e7-8d6a-925d1e778d7e]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7d020da8-109b-4ab6-95f4-7dfcef7b5119
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
statistics          : {collisions=0, rx_bytes=3068516318, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72688535, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : f9ce74b9-4105-4f37-9515-e7d2e75649cf
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5264406, tx_dropped=0, tx_errors=0, tx_packets=56126}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 94bdaa0b-65aa-40e7-8d6a-925d1e778d7e
admin_state         : up
duplex              : full
ifindex             : 702
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 90b8c2f7c08eab4aea41601e57d4eee021ef5561
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Mon Mar 24 17:34:48 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Mon Mar 24 17:34:48 2014 -0700

    datapath: Avoid assigning a NULL pointer to flow actions.
    
    Flow SET can accept an empty set of actions, with the intended
    semantics of leaving existing actions unmodified.  This seems to have
    been brokin after OVS 1.7, as we have assigned the flow's actions
    pointer to NULL in this case, but we never check for the NULL pointer
    later on.  This patch restores the intended behavior and documents it
    in the include/linux/openvswitch.h.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
