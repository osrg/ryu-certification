---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8a320c58-8f8a-4cd2-bdbf-3db272c26418
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
_uuid               : 04a7eb6b-c3cb-48f0-b7d9-52ed08d061e2
controller          : [8ec77349-e1d4-4d30-a7b5-bd9ff3c2488e]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2bd632dd-184e-498f-97c8-2a5830e56139, 6f66c9a4-2fb1-41cf-84ad-ee9df1c687ab, 98bdea3c-4516-4c5c-a8fc-5e2041d6cefc, bcbc2cdc-e929-4fe3-a243-b29cc27aa1b1]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8ec77349-e1d4-4d30-a7b5-bd9ff3c2488e
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="6", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6f66c9a4-2fb1-41cf-84ad-ee9df1c687ab
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [38493139-5e9e-4a1e-9341-1fb1f33e811c]
name                : "eth22"

_uuid               : bcbc2cdc-e929-4fe3-a243-b29cc27aa1b1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a237b46a-bad8-434f-9070-bb7be8d1f0cd]
name                : "eth23"

_uuid               : 98bdea3c-4516-4c5c-a8fc-5e2041d6cefc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [edd4ad5f-faf5-4d95-b686-793575a360f8]
name                : "eth21"

_uuid               : 2bd632dd-184e-498f-97c8-2a5830e56139
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [32e95d62-43ab-472f-8478-ea7facca10c6]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 38493139-5e9e-4a1e-9341-1fb1f33e811c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31225901235, tx_dropped=0, tx_errors=0, tx_packets=20851349}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 32e95d62-43ab-472f-8478-ea7facca10c6
admin_state         : down
duplex              : full
ifindex             : 822
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

_uuid               : a237b46a-bad8-434f-9070-bb7be8d1f0cd
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

_uuid               : edd4ad5f-faf5-4d95-b686-793575a360f8
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
statistics          : {collisions=0, rx_bytes=46725560045, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31224428, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
