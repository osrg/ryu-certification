---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
915918df-3de8-4f15-992b-1185321f0092
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c4e8ec6e-20fc-49ee-a276-05333c2600a1
controller          : [5883aa6e-e34b-4b47-977e-c7e699479061]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [13d5bc10-d47f-4881-9350-986880972f68, 27aca0b4-9e00-4ac6-b6de-0e6e208329ce, 79c20342-a266-4add-ab49-91a633454bcc, a5252fc7-7756-4370-97f8-93eb697ecda7]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5883aa6e-e34b-4b47-977e-c7e699479061
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 27aca0b4-9e00-4ac6-b6de-0e6e208329ce
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a55eeaca-7dba-440d-8ee4-45df85c0369f]
name                : "eth22"

_uuid               : 13d5bc10-d47f-4881-9350-986880972f68
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [59b95182-f909-41d3-bb5d-a86c84818979]
name                : "br0"

_uuid               : 79c20342-a266-4add-ab49-91a633454bcc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5f0cd068-35ea-48eb-98ec-49de0dd5defa]
name                : "eth21"

_uuid               : a5252fc7-7756-4370-97f8-93eb697ecda7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [181725b1-66f1-460c-b22a-d396b32e9037]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 5f0cd068-35ea-48eb-98ec-49de0dd5defa
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
statistics          : {collisions=0, rx_bytes=44736334914, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29887102, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 181725b1-66f1-460c-b22a-d396b32e9037
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=8223226500, tx_dropped=0, tx_errors=0, tx_packets=5482151}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a55eeaca-7dba-440d-8ee4-45df85c0369f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30330440240, tx_dropped=0, tx_errors=0, tx_packets=20248928}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 59b95182-f909-41d3-bb5d-a86c84818979
admin_state         : down
duplex              : full
ifindex             : 758
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
commit b89c678b7a267ec004ae292c8f0ee0c3f0ccb6d5
Author:     Andy Zhou &lt;azhou@ovn.org&gt;
AuthorDate: Fri Jan 29 17:48:50 2016 -0800
Commit:     Andy Zhou &lt;azhou@ovn.org&gt;
CommitDate: Tue Feb 2 12:01:14 2016 -0800

    dpif-netdev: optmizing emc_processing&#40;&#41;
    
    Commit d262ac2c60ce1da7b477737f70e8efd38b32502d introduced a slight
    performance drop for the fast path, where every packets hits the
    emc cache.  This patch removes that performance drop by only reloading
    the key pointer on emc cache miss.
    
    Signed-off-by: Andy Zhou &lt;azhou@ovn.org&gt;
    Acked-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>
