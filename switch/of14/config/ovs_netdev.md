---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b51a89cc-6f71-4b47-8ddf-ac16c8a0575b
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0c2ae7a1-ff33-40a1-bd70-ebcf45ab1c8f
controller          : [761d5819-dfdb-42f4-a943-84d6347ef832]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [014c56e3-b714-485e-bbbf-cadd1311b287, 39a2d17f-b775-46b0-991a-77182e80bba5, 5453fc22-f793-42d2-95d4-e481c4c97c45, bb7d00e1-5a37-42b6-977d-afc07376ef98]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 761d5819-dfdb-42f4-a943-84d6347ef832
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="16", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : bb7d00e1-5a37-42b6-977d-afc07376ef98
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7550e6c3-e809-4f9d-93f7-656093b7b69e]
name                : "br0"

_uuid               : 5453fc22-f793-42d2-95d4-e481c4c97c45
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3ec870e3-1db5-456f-9336-1e9d12a88e9b]
name                : "eth22"

_uuid               : 014c56e3-b714-485e-bbbf-cadd1311b287
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b176adfd-860e-4b5d-9493-4bbb5fc8afd1]
name                : "eth21"

_uuid               : 39a2d17f-b775-46b0-991a-77182e80bba5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [423b6e3e-4ba8-4762-ae79-eab97a8189e2]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b176adfd-860e-4b5d-9493-4bbb5fc8afd1
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
statistics          : {collisions=0, rx_bytes=48129790253, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=32168480, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 423b6e3e-4ba8-4762-ae79-eab97a8189e2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10766080500, tx_dropped=0, tx_errors=0, tx_packets=7177387}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7550e6c3-e809-4f9d-93f7-656093b7b69e
admin_state         : down
duplex              : full
ifindex             : 874
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

_uuid               : 3ec870e3-1db5-456f-9336-1e9d12a88e9b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31858429347, tx_dropped=0, tx_errors=0, tx_packets=21276889}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5fec03b1178d21f98fb8d10b2b3d7be1e64da511
Author:     Ben Pfaff &lt;blp@ovn.org&gt;
AuthorDate: Thu Mar 10 17:46:10 2016 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Thu Mar 10 21:10:25 2016 -0800

    Document how to match any packet with a VLAN header.
    
    This one is actually useful, I don't know how I omitted it whenever I wrote
    this documentation.
    
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
    Acked-by: Justin Pettit &lt;jpettit@ovn.org&gt;
</pre>
