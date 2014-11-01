---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a7108640-5cef-489b-a553-55736dd56cdf
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 6686c06f-84ee-4a88-9a04-de47a8ce044e
controller          : [806bcf69-c3f0-460c-ab56-c166ed8f369d]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [020774f5-528d-4dbe-9b43-8866809446c3, 368cf8a9-5265-4a88-b6f9-a7efe67276fe, 66ae3e5d-d269-467b-8926-410d0f064dcb, 8020a22e-c5bf-471c-8749-8e5b73fda44b]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 806bcf69-c3f0-460c-ab56-c166ed8f369d
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=681, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 368cf8a9-5265-4a88-b6f9-a7efe67276fe
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [284cf773-b464-412d-bf4d-412580483c7b]
name                : eth23

_uuid               : 66ae3e5d-d269-467b-8926-410d0f064dcb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a0034979-b5a7-45e1-a5cc-d24d39ff7ae6]
name                : eth22

_uuid               : 020774f5-528d-4dbe-9b43-8866809446c3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b6993c93-c7bc-4477-a607-9ea2b2caeaa9]
name                : br0

_uuid               : 8020a22e-c5bf-471c-8749-8e5b73fda44b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bd659cbc-bd4f-47b3-8297-4d3ed7dd68cc]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : bd659cbc-bd4f-47b3-8297-4d3ed7dd68cc
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
statistics          : {collisions=0, rx_bytes=257851683345, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=172006688, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a0034979-b5a7-45e1-a5cc-d24d39ff7ae6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=158104696352, tx_dropped=0, tx_errors=0, tx_packets=105450862}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 284cf773-b464-412d-bf4d-412580483c7b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=13770675000, tx_dropped=0, tx_errors=0, tx_packets=9180450}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b6993c93-c7bc-4477-a607-9ea2b2caeaa9
admin_state         : down
duplex              : full
ifindex             : 311
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
commit 712b4d2470ed2e8cfe6bb16080d7e9d54003061a
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Fri Oct 31 14:14:56 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Fri Oct 31 16:28:58 2014 -0700

    test-classifier: Ensure priority is not INT_MIN.
    
    Classifier reserves the priority value INT_MIN for its own use.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
