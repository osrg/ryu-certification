---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b299fcd5-8250-41ec-9a03-b53d914844a4
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 32655864-e19b-435b-b347-b7f50e3c6752
controller          : [331a6968-bcf1-475a-8a29-4bcb2b6e53be]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [9778306d-cf42-4165-98a8-2e9b29469133, a3d083c3-7565-44f6-bec3-1254a23526fc, adcd1a02-7717-4c52-9ab4-f5a5072ccd57, d24c3b09-9ba3-4078-b9d2-d6350716d0a9]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 331a6968-bcf1-475a-8a29-4bcb2b6e53be
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d24c3b09-9ba3-4078-b9d2-d6350716d0a9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7b626c1e-233d-4cfa-a962-78bcbcf9d93c]
name                : "eth23"

_uuid               : 9778306d-cf42-4165-98a8-2e9b29469133
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2cb967fc-e130-4893-9f61-7772aa77c1c1]
name                : "eth21"

_uuid               : adcd1a02-7717-4c52-9ab4-f5a5072ccd57
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c8dfed97-8db1-4b6c-bafc-f692c6839a89]
name                : "br0"

_uuid               : a3d083c3-7565-44f6-bec3-1254a23526fc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d9690c2e-1741-4ac7-ad45-b235e4d2f9a6]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2cb967fc-e130-4893-9f61-7772aa77c1c1
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
statistics          : {collisions=0, rx_bytes=45906476566, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30673771, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d9690c2e-1741-4ac7-ad45-b235e4d2f9a6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30856961812, tx_dropped=0, tx_errors=0, tx_packets=20603147}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7b626c1e-233d-4cfa-a962-78bcbcf9d93c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9100432500, tx_dropped=0, tx_errors=0, tx_packets=6066955}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c8dfed97-8db1-4b6c-bafc-f692c6839a89
admin_state         : down
duplex              : full
ifindex             : 796
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
commit d5579e480863ed07402d400877cf37e701419b9e
Author:     Andy Zhou &lt;azhou@ovn.org&gt;
AuthorDate: Fri Feb 12 10:36:51 2016 -0800
Commit:     Andy Zhou &lt;azhou@ovn.org&gt;
CommitDate: Fri Feb 12 12:39:07 2016 -0800

    lib: Remove unused function prototypes
    
    Found by inspection.
    
    Signed-off-by: Andy Zhou &lt;azhou@ovn.org&gt;
    Acked-by: Russell Bryant &lt;russell@ovn.org&gt;
</pre>
