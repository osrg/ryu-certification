---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
381bdc81-a523-4ba6-bfae-881f853976f8
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a5419aa5-97ba-4ed7-a6dc-7aae34af2ae4
controller          : [ac834e53-d003-4dbe-a9ec-3ad507db02bf]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3450c998-543f-48a7-807e-83941edb3379, 44461b84-fef3-47ab-9249-cc75df051db3, 7c607c35-836b-4fec-9755-e11ef831ca57, 9d4cb1a2-4e72-4eb3-8dc1-fb0574edc96a]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ac834e53-d003-4dbe-a9ec-3ad507db02bf
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="757", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 44461b84-fef3-47ab-9249-cc75df051db3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ede99bc7-3b56-4f15-90d4-a992179a8501]
name                : "eth23"

_uuid               : 3450c998-543f-48a7-807e-83941edb3379
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b2b28ae7-279b-480f-a29f-c08589819b92]
name                : "br0"

_uuid               : 7c607c35-836b-4fec-9755-e11ef831ca57
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d08eb162-d0b5-4345-82de-ce5d886ba3a4]
name                : "eth22"

_uuid               : 9d4cb1a2-4e72-4eb3-8dc1-fb0574edc96a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [276e57b0-b5fc-404b-b53f-4c3140b83db2]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 276e57b0-b5fc-404b-b53f-4c3140b83db2
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
statistics          : {collisions=0, rx_bytes=37492892971, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=25017994, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d08eb162-d0b5-4345-82de-ce5d886ba3a4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=27033582442, tx_dropped=0, tx_errors=0, tx_packets=18032538}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b2b28ae7-279b-480f-a29f-c08589819b92
admin_state         : down
duplex              : full
ifindex             : 561
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

_uuid               : ede99bc7-3b56-4f15-90d4-a992179a8501
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2830731000, tx_dropped=0, tx_errors=0, tx_packets=1887154}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 12c96b8af6d9b738a05e93f37941083016d06bf8
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Oct 13 09:44:18 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Oct 13 13:58:43 2015 -0700

    appveyor.yml: Remove from docs.
    
    It's not documentation.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
