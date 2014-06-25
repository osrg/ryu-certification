---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
09590937-ca8a-4384-8ddc-783a5148aa94
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 901d1c33-9e25-405e-933e-d7cdfd318154
controller          : [9828e770-e6e5-4c48-97ea-839d7e31d394]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5142b178-9c71-472f-a6d9-a43add62cd06, 778ffd11-62b0-4225-89cd-3f7d8afa45a8, 84b13504-0bca-4971-ae84-2cda7821ee3e, edc86d5b-cbac-4f46-9183-8b6da8c369bf]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9828e770-e6e5-4c48-97ea-839d7e31d394
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=657, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 84b13504-0bca-4971-ae84-2cda7821ee3e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d262d95f-003b-4980-ac49-a96d20592b42]
name                : eth23

_uuid               : 5142b178-9c71-472f-a6d9-a43add62cd06
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b3b33df8-2f7e-413d-8d21-ff8d14dcc211]
name                : eth22

_uuid               : 778ffd11-62b0-4225-89cd-3f7d8afa45a8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dc1124b0-b789-4001-9348-d1011d0bd823]
name                : eth21

_uuid               : edc86d5b-cbac-4f46-9183-8b6da8c369bf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [35dcfe60-f544-4d0e-99f1-b9cefa21dced]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : dc1124b0-b789-4001-9348-d1011d0bd823
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
statistics          : {collisions=0, rx_bytes=667750102, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=92212605, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b3b33df8-2f7e-413d-8d21-ff8d14dcc211
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2766936472, tx_dropped=0, tx_errors=0, tx_packets=36258710}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 35dcfe60-f544-4d0e-99f1-b9cefa21dced
admin_state         : down
duplex              : full
ifindex             : 717
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

_uuid               : d262d95f-003b-4980-ac49-a96d20592b42
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2759140284, tx_dropped=0, tx_errors=0, tx_packets=13293357}
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
