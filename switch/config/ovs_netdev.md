---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
89e3342c-54b4-4f6d-9923-8d95fd8fd6b9
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 844900c6-7d3e-4fe6-91f6-39d556ea5f40
controller          : [91614390-b305-4e80-beb7-4ca36f147256]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [8281d759-e1be-49ba-986a-d28c5dbc2359, 8852fd94-ba10-45ea-84dc-a2eb6d3ead19, 8a1b773d-4e71-43cb-9365-29694e9ea73a, a4e94a27-2eaf-461c-8c7f-ac18daca20f6]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 91614390-b305-4e80-beb7-4ca36f147256
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="767", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8852fd94-ba10-45ea-84dc-a2eb6d3ead19
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ceca32a3-0b00-46a6-be71-19c4baf901cd]
name                : "br0"

_uuid               : 8281d759-e1be-49ba-986a-d28c5dbc2359
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1cb4499e-119a-4f8d-aa4d-6761231145e4]
name                : "eth23"

_uuid               : 8a1b773d-4e71-43cb-9365-29694e9ea73a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2ae8a551-8b36-4600-9c81-f91250b0abd5]
name                : "eth21"

_uuid               : a4e94a27-2eaf-461c-8c7f-ac18daca20f6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9ac14054-34cc-4003-a67a-e50ae3ce1177]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9ac14054-34cc-4003-a67a-e50ae3ce1177
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28192420858, tx_dropped=0, tx_errors=0, tx_packets=18811159}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 2ae8a551-8b36-4600-9c81-f91250b0abd5
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=40067289929, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26748418, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1cb4499e-119a-4f8d-aa4d-6761231145e4
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4760185500, tx_dropped=0, tx_errors=0, tx_packets=3173457}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ceca32a3-0b00-46a6-be71-19c4baf901cd
admin_state         : down
duplex              : full
ifindex             : 605
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a422ea1d6011048fa722b199437801338a9560cb
Author:     Sairam Venugopal &lt;vsairam@vmware.com&gt;
AuthorDate: Mon Oct 26 16:48:41 2015 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Tue Oct 27 13:49:03 2015 -0700

    datapath-windows: STT - Enable support for TCP Segmentation offloads
    
    Add support to STT - Encap and Decap functions to reassemble the packet
    fragments. Also add support to offload the packet to NDIS.
    
    Signed-off-by: Sairam Venugopal &lt;vsairam@vmware.com&gt;
    Acked-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
