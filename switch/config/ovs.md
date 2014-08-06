---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
82811119-3ff0-43a5-b59e-51f3ffa061b0
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b250c491-1966-4341-b288-9c753739601c
controller          : [997b2b2c-82d4-424d-8129-39bf633059eb]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [76d5baa3-6c79-4917-bb9f-3195c9b96a12, 7ec63dac-b5b4-4504-bfaf-2c71c6d3fa02, cd31e432-a3f3-4b68-9d87-39cb3e7c7618, f85249b3-8c00-412f-84f7-78de168f1074]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 997b2b2c-82d4-424d-8129-39bf633059eb
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=672, sec_since_disconnect=7, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7ec63dac-b5b4-4504-bfaf-2c71c6d3fa02
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [136a1b16-3a8f-4e0d-a99d-8018ef73a06a]
name                : eth22

_uuid               : cd31e432-a3f3-4b68-9d87-39cb3e7c7618
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [91251972-a59d-47b8-848d-e6d3485d75c9]
name                : eth21

_uuid               : f85249b3-8c00-412f-84f7-78de168f1074
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f5c3c4f8-d322-422f-b26d-69800ce18f1c]
name                : br0

_uuid               : 76d5baa3-6c79-4917-bb9f-3195c9b96a12
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6b68a4fe-571f-4530-a4e5-5bfea423b890]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f5c3c4f8-d322-422f-b26d-69800ce18f1c
admin_state         : down
ifindex             : 75
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

_uuid               : 136a1b16-3a8f-4e0d-a99d-8018ef73a06a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1188609296, tx_dropped=0, tx_errors=0, tx_packets=49480829}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 91251972-a59d-47b8-848d-e6d3485d75c9
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
statistics          : {collisions=0, rx_bytes=1957128995, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=84368624, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6b68a4fe-571f-4530-a4e5-5bfea423b890
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2598024000, tx_dropped=0, tx_errors=0, tx_packets=1732016}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
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
