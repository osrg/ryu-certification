---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f19dc939-9539-45a7-80a8-f8f115118df7
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
_uuid               : 056d62d3-c6f2-4d61-b9b3-62cf8e0e54a0
controller          : [a4a4ad83-64a7-40e7-ab3a-b49df6427237]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5d696394-1016-48b7-bdb0-b4f29e67e7b2, b243132f-c2f5-4b78-be1b-01663ca920d8, cd3caddc-eddf-4e4e-af41-80798591068a, d5e333f1-98fa-42d2-b95e-3cfe80ae974c]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a4a4ad83-64a7-40e7-ab3a-b49df6427237
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=656, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5d696394-1016-48b7-bdb0-b4f29e67e7b2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1c07b677-8f90-45a6-b732-20e9fc364191]
name                : eth22

_uuid               : cd3caddc-eddf-4e4e-af41-80798591068a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8f2fb21a-0fee-4c73-9bec-86b21bad3506]
name                : eth21

_uuid               : d5e333f1-98fa-42d2-b95e-3cfe80ae974c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [be6b9945-3a2a-4b5d-bf2a-277454c47f8c]
name                : eth23

_uuid               : b243132f-c2f5-4b78-be1b-01663ca920d8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2816f059-aac9-463d-9740-a4306ee720f9]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2816f059-aac9-463d-9740-a4306ee720f9
admin_state         : down
ifindex             : 91
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

_uuid               : be6b9945-3a2a-4b5d-bf2a-277454c47f8c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3392133000, tx_dropped=0, tx_errors=0, tx_packets=2261422}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8f2fb21a-0fee-4c73-9bec-86b21bad3506
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
statistics          : {collisions=0, rx_bytes=2892015159, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=84996931, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 1c07b677-8f90-45a6-b732-20e9fc364191
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1516276432, tx_dropped=0, tx_errors=0, tx_packets=49701617}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 694ffeccf133d20765107ac2738e325ae9b669d3
Author:     Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
AuthorDate: Fri Aug 8 10:15:57 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Fri Aug 8 10:15:57 2014 -0700

    lib/flow: Update FLOW_WC_SEQ to skip assertions on miniflow_extract&#40;&#41;
    
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
