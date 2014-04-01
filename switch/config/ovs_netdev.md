---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7424a453-860b-415c-bf5b-ab7de0ce6c56
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
_uuid               : b5e3a60c-95de-491b-b656-513355ac8e74
controller          : [b1536605-61ce-4e80-a1da-0aa35eeaa56e]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [671b9e13-1b3f-4399-b13d-fe4ef3020b5c, 854e81db-69fe-41e1-87a2-b848916159bd, da63b2a7-ce5d-40d8-ae70-9826a7399309]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b1536605-61ce-4e80-a1da-0aa35eeaa56e
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=307, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 671b9e13-1b3f-4399-b13d-fe4ef3020b5c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [37f8ed9a-4076-473d-9411-2f3369b39b9b]
name                : eth8

_uuid               : 854e81db-69fe-41e1-87a2-b848916159bd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2e4fea63-e354-4fa2-91b5-e734a60c4b1a]
name                : eth7

_uuid               : da63b2a7-ce5d-40d8-ae70-9826a7399309
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9abf1183-cec8-4621-94c7-72d7722efba9]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 37f8ed9a-4076-473d-9411-2f3369b39b9b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6456754, tx_dropped=0, tx_errors=0, tx_packets=68824}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 2e4fea63-e354-4fa2-91b5-e734a60c4b1a
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
statistics          : {collisions=0, rx_bytes=3072545347, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72729415, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 9abf1183-cec8-4621-94c7-72d7722efba9
admin_state         : up
duplex              : full
ifindex             : 837
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
commit d7aab66192b34473a8b12f31113ce7cf8b61b9a9
Author:     Jason Kölker &lt;jason@koelker.net&gt;
AuthorDate: Mon Mar 31 23:34:14 2014 +0000
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Tue Apr 1 08:21:50 2014 -0700

    rhel: Add Patch Port support to initscripts
    
    Allows setting up type=patch ports through sysconfig ifcfg-* files.
    
    Signed-off-by: Jason Kölker &lt;jason@koelker.net&gt;
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Flavio Leitner &lt;fbl@redhat.com&gt;
</pre>
