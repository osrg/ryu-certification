---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a7d06aa2-1227-4e95-8039-e13125c30270
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 1e7c037c-d4f1-4be0-ba7b-0ad2887b25a4
controller          : [447df7a5-7bfe-41bf-954d-ac832bc6ecb4]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [17733990-24eb-4956-83d6-a87503b4aaa7, 2ae41006-104a-49ad-9dd8-e01d69bdc7aa, 95bbea18-004e-489c-a514-da101c3b79c3]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 447df7a5-7bfe-41bf-954d-ac832bc6ecb4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=371, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 95bbea18-004e-489c-a514-da101c3b79c3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [feaee094-24b7-4ded-9700-4e5a52735fbc]
name                : eth8

_uuid               : 17733990-24eb-4956-83d6-a87503b4aaa7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7d531e93-2a40-46bc-8df7-cfb0e5d9c15e]
name                : br0

_uuid               : 2ae41006-104a-49ad-9dd8-e01d69bdc7aa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [830f3412-2a82-45f5-889b-83267b641462]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : feaee094-24b7-4ded-9700-4e5a52735fbc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3329634, tx_dropped=0, tx_errors=0, tx_packets=35529}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 830f3412-2a82-45f5-889b-83267b641462
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
statistics          : {collisions=0, rx_bytes=3061962412, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72622052, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 7d531e93-2a40-46bc-8df7-cfb0e5d9c15e
admin_state         : up
duplex              : full
ifindex             : 462
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
commit f35c2d60cd793f424ed0958505d8ec40a5878520
Author:     Pravin Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Thu Feb 6 12:31:13 2014 -0800
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Fri Mar 7 04:03:53 2014 -0800

    netdev-linux: Remove unnecessary header.
    
    netdev-linux does not depend on linux kernel version. So
    remove header file include.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
