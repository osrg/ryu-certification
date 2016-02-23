---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d87bbe2f-7efe-4070-b666-37d64f6782ac
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
_uuid               : eae246db-bb43-42ae-a028-7d18d3a83f4d
controller          : [ca093a34-9749-4910-8f02-71846ebf09eb]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [127cfce9-112d-4fcf-a030-8a8ec66467a6, aed2558e-1f6a-47eb-8ac9-7ce7cd872f1a, bcaa5658-1e46-4cd4-8a42-5eeb5dcccb14, eb55a979-94ca-482f-96a0-1850bc247cfb]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ca093a34-9749-4910-8f02-71846ebf09eb
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="12", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : bcaa5658-1e46-4cd4-8a42-5eeb5dcccb14
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [516faa36-f627-44c2-81e8-ae46caba40c8]
name                : "eth21"

_uuid               : eb55a979-94ca-482f-96a0-1850bc247cfb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [37bf048c-aec1-4a74-88be-bac8b81c0509]
name                : "br0"

_uuid               : 127cfce9-112d-4fcf-a030-8a8ec66467a6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4b771bee-3438-4f96-bc99-4a987708ac6d]
name                : "eth23"

_uuid               : aed2558e-1f6a-47eb-8ac9-7ce7cd872f1a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bdfba8bb-33fc-409a-988d-1adedbb6bd6f]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 37bf048c-aec1-4a74-88be-bac8b81c0509
admin_state         : down
duplex              : full
ifindex             : 824
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

_uuid               : 4b771bee-3438-4f96-bc99-4a987708ac6d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9714079500, tx_dropped=0, tx_errors=0, tx_packets=6476053}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 516faa36-f627-44c2-81e8-ae46caba40c8
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
statistics          : {collisions=0, rx_bytes=46725560303, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31224431, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : bdfba8bb-33fc-409a-988d-1adedbb6bd6f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31225901493, tx_dropped=0, tx_errors=0, tx_packets=20851352}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ca7e7bee86b4ee821d61b58bf15c89a9d8a3cb30
Author:     Mauricio Vásquez &lt;mauricio.vasquezbernal@studenti.polito.it&gt;
AuthorDate: Sat Jan 23 22:20:13 2016 -0500
Commit:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
CommitDate: Tue Feb 23 10:02:17 2016 -0800

    lib/netdev-dpdk: increase ring name length for dpdkr ports
    
    A ring name length of 10 characters is not enough for dpdkr ports
    starting from dpdkr10, then it is increased to RTE_RING_NAMESIZE
    characters.
    
    Signed-off-by: Mauricio Vasquez B &lt;mauricio.vasquezbernal@studenti.polito.it&gt;
    Acked-by: Aaron Conole &lt;aconole@redhat.com&gt;
    Acked-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>
