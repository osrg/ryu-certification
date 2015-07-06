---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
99054186-7a63-483c-9584-d22092424d4e
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
_uuid               : a3bfb085-5d40-4b41-a673-aa59672dd9bd
controller          : [89f93b80-d88e-4529-8ace-66ba5af2711d]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [25fdc957-21fb-4a4e-8971-b3e2b14d78ad, 57efa48e-b33a-48b5-afa2-c0792c58adc9, 97dfd4ed-aacf-46f1-b64d-a00de8b13a08, 9ab2d473-934f-4b6f-a0b9-b53cf1d8aab1]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 89f93b80-d88e-4529-8ace-66ba5af2711d
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 97dfd4ed-aacf-46f1-b64d-a00de8b13a08
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [50d847c3-e6c6-49e7-9173-8c5b58b00e86]
name                : "eth21"

_uuid               : 57efa48e-b33a-48b5-afa2-c0792c58adc9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0a694527-ecf1-43ea-9b71-b27bde3a0f8a]
name                : "eth22"

_uuid               : 9ab2d473-934f-4b6f-a0b9-b53cf1d8aab1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [355db466-ee95-431e-8865-6ee612df54af]
name                : "eth23"

_uuid               : 25fdc957-21fb-4a4e-8971-b3e2b14d78ad
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f6d6083a-d82b-4670-b733-f91d25c13499]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 355db466-ee95-431e-8865-6ee612df54af
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1176922500, tx_dropped=0, tx_errors=0, tx_packets=784615}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f6d6083a-d82b-4670-b733-f91d25c13499
admin_state         : down
duplex              : full
ifindex             : 225
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

_uuid               : 50d847c3-e6c6-49e7-9173-8c5b58b00e86
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
statistics          : {collisions=0, rx_bytes=24024581534, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16026376, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 0a694527-ecf1-43ea-9b71-b27bde3a0f8a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18089315792, tx_dropped=0, tx_errors=0, tx_packets=12064077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 2494ccd78fa0d5cfb3d855abd6bf351acf27e401
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Tue Jun 30 16:43:03 2015 -0700
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Mon Jul 6 10:17:37 2015 -0700

    odp-util: Share fields between odp and dpif_backer.
    
    Datapath support for some flow key fields is used inside ofproto-dpif as
    well as odp-util. Share these fields using the same structure.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
