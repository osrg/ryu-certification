---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3232be9a-9ff9-4c41-bbe8-b192d39ae273
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : acbe211d-7c2d-4d7a-b555-97deffd3bacd
controller          : [2efacb55-49b7-44e7-99e9-61b26fde6bab]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [043c2e09-a44a-44b7-935d-3baca27dc59c, 185ebe26-0eec-4ecc-9774-4a96a035c7ca, 68899f6e-7b57-4295-83df-8885936d4e79, 9adeda29-e467-4276-8fbd-4f7d315b7914]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2efacb55-49b7-44e7-99e9-61b26fde6bab
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 043c2e09-a44a-44b7-935d-3baca27dc59c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f36ddbd8-941b-4265-b3a6-9fa9248be65a]
name                : "eth22"

_uuid               : 9adeda29-e467-4276-8fbd-4f7d315b7914
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [726e1bba-75ce-4949-b26a-26340b822d9b]
name                : "eth23"

_uuid               : 185ebe26-0eec-4ecc-9774-4a96a035c7ca
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e5a82e7c-a388-47d3-80a0-efa4fa095c8d]
name                : "br0"

_uuid               : 68899f6e-7b57-4295-83df-8885936d4e79
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fd5a52a7-0409-42c2-8be1-a1ceac0d463e]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e5a82e7c-a388-47d3-80a0-efa4fa095c8d
admin_state         : down
duplex              : full
ifindex             : 76
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

_uuid               : f36ddbd8-941b-4265-b3a6-9fa9248be65a
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

_uuid               : 726e1bba-75ce-4949-b26a-26340b822d9b
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

_uuid               : fd5a52a7-0409-42c2-8be1-a1ceac0d463e
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 8f19f0a70352dfa555cffa4f7f34dab22870dc49
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Wed May 20 13:46:01 2015 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Fri May 22 15:05:04 2015 -0700

    odp-util: always output recirc_id in hex
    
    The match is in hex, this makes it more consistent.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
