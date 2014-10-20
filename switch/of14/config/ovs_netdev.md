---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fbb39b23-16c6-429c-8afa-4d4e682a327e
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 048ce2d5-f0f3-47b4-996f-334aba671089
controller          : [e544bc3e-429e-431c-ab2f-ef2761f47662]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1f197cd6-f0b6-4fd9-8933-51b3d467e10d, 34a5551a-ceca-4bd9-b2ab-c62b0e4ac5ad, 55d232dd-2d9e-41f8-b812-61bbe796c792, 9948436d-c853-48f4-b282-ee3a27da5fec]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e544bc3e-429e-431c-ab2f-ef2761f47662
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=722, sec_since_disconnect=6, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 55d232dd-2d9e-41f8-b812-61bbe796c792
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [99049fcd-dfee-4e03-81ad-d1b1d4299c2a]
name                : eth22

_uuid               : 9948436d-c853-48f4-b282-ee3a27da5fec
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c37b9aaa-093a-4a04-bedd-e81703fd0f26]
name                : eth23

_uuid               : 1f197cd6-f0b6-4fd9-8933-51b3d467e10d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c82d3163-0e27-4c18-b540-16d80cad8ce8]
name                : br0

_uuid               : 34a5551a-ceca-4bd9-b2ab-c62b0e4ac5ad
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [566dd6a4-a4c5-4462-9ea6-87c52773de8b]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 566dd6a4-a4c5-4462-9ea6-87c52773de8b
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
statistics          : {collisions=0, rx_bytes=1783485537, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=170215864, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 99049fcd-dfee-4e03-81ad-d1b1d4299c2a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2255818732, tx_dropped=0, tx_errors=0, tx_packets=104624277}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c37b9aaa-093a-4a04-bedd-e81703fd0f26
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3212951908, tx_dropped=0, tx_errors=0, tx_packets=7868591}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c82d3163-0e27-4c18-b540-16d80cad8ce8
admin_state         : down
duplex              : full
ifindex             : 267
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f0d2e458f12b6117ff443d3a9e79c414b473c5e4
Author:     Thomas Graf &lt;tgraf@noironetworks.com&gt;
AuthorDate: Mon Oct 20 19:23:19 2014 +0200
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Mon Oct 20 11:22:17 2014 -0700

    Makefile.am: Properly indent INSTALL.DPDK
    
    Signed-off-by: Thomas Graf &lt;tgraf@noironetworks.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
