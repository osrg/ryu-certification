---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7b204e6b-3201-46aa-9f0c-91873d14485e
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 5032a99a-b0f3-4c08-be1f-c065f5bc976d
controller          : [8f0414e4-67f3-4e8d-8fb2-c0b2b00af81c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [11c6a40a-2557-4db8-8c94-687f894addce, 5c79d26a-2eb8-420c-a784-66775a6cad20, a9a8bab8-f096-47c7-bb11-82c92bb304cc, c108d41c-1928-4990-b3d4-2d5a9c89b42e]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8f0414e4-67f3-4e8d-8fb2-c0b2b00af81c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c108d41c-1928-4990-b3d4-2d5a9c89b42e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7205c220-3446-4815-86db-933d3e7adfb0]
name                : "br0"

_uuid               : a9a8bab8-f096-47c7-bb11-82c92bb304cc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [646ca1aa-95ec-4899-977d-bde3e8097af3]
name                : "eth21"

_uuid               : 11c6a40a-2557-4db8-8c94-687f894addce
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [514f87d4-1f62-4018-a170-122ac0afe507]
name                : "eth23"

_uuid               : 5c79d26a-2eb8-420c-a784-66775a6cad20
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bab139d2-ea8e-45b5-a2cc-627a2b83d660]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 514f87d4-1f62-4018-a170-122ac0afe507
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6380938500, tx_dropped=0, tx_errors=0, tx_packets=4253959}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7205c220-3446-4815-86db-933d3e7adfb0
admin_state         : down
duplex              : full
ifindex             : 678
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

_uuid               : bab139d2-ea8e-45b5-a2cc-627a2b83d660
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29224784213, tx_dropped=0, tx_errors=0, tx_packets=19505094}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 646ca1aa-95ec-4899-977d-bde3e8097af3
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
statistics          : {collisions=0, rx_bytes=42278920719, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28235019, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ab58aa48a198c3210021070f82042d4dea1e4b41
Author:     Alin Serdean &lt;aserdean@cloudbasesolutions.com&gt;
AuthorDate: Fri Dec 11 14:59:07 2015 +0000
Commit:     Justin Pettit &lt;jpettit@ovn.org&gt;
CommitDate: Fri Dec 11 14:36:14 2015 -0800

    datapath-windows: Cleanup Stt.c
    
    Remove double include for Flow.h and sort the includes alphabetically.
    Also remove tabs.
    
    Found by inspection.
    
    Signed-off-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Acked-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Acked-by: Sairam Venugopal &lt;vsairam@vmware.com&gt;
    Acked-by: Sorin Vinturis &lt;svinturis@cloudbasesolutions.com&gt;
    Signed-off-by: Justin Pettit &lt;jpettit@ovn.org&gt;
</pre>
