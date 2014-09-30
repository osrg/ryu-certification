---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6d7c31a0-1e1b-4492-920a-fd895474d50a
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
_uuid               : f89155cf-2bc3-4610-a1e4-45ff60c7e31e
controller          : [877cc52c-1747-4c2e-a3fb-2aec9e2a4720]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [538a5fec-22ed-41d9-a6d0-a369c27e868e, 9af241a0-5e6c-4700-9d67-fc2fa5771c92, 9e1ab161-2789-4cda-b82c-2a80d6ca246a, f76a41cb-c6ad-4527-ae32-f3fce991cef3]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 877cc52c-1747-4c2e-a3fb-2aec9e2a4720
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=662, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 538a5fec-22ed-41d9-a6d0-a369c27e868e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [52d7f53a-b2f2-45c9-9420-9a3cd73d1686]
name                : eth22

_uuid               : 9af241a0-5e6c-4700-9d67-fc2fa5771c92
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e1bd7d10-5366-46a8-b640-0e55d09b7252]
name                : eth21

_uuid               : 9e1ab161-2789-4cda-b82c-2a80d6ca246a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bf2c3082-036c-4cb8-a7a1-3cb6faa01405]
name                : eth23

_uuid               : f76a41cb-c6ad-4527-ae32-f3fce991cef3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [73cd3c36-d13f-4d76-a1c5-8404b483572f]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e1bd7d10-5366-46a8-b640-0e55d09b7252
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
statistics          : {collisions=0, rx_bytes=1776861605, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=75689610, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 73cd3c36-d13f-4d76-a1c5-8404b483572f
admin_state         : down
duplex              : full
ifindex             : 190
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

_uuid               : bf2c3082-036c-4cb8-a7a1-3cb6faa01405
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3641054204, tx_dropped=0, tx_errors=0, tx_packets=5290681}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 52d7f53a-b2f2-45c9-9420-9a3cd73d1686
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2992483162, tx_dropped=0, tx_errors=0, tx_packets=47834700}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ee8627fa801a23084f211d5c6523b9c46c6d13e7
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Fri Sep 26 15:05:40 2014 +0000
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Tue Sep 30 11:28:48 2014 -0700

    INSTALL.DPDK: Update DPDK related documentation.
    
    This commit updates the DPDK related documentation to reflect
    the pmd thread multi-threading work.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
</pre>
