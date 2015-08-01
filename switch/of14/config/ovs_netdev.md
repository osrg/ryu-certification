---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
cf3dd16b-976a-45da-ad60-30256e027a0d
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 3b6f7287-eb09-49c6-ad56-f3b8d4504cb3
controller          : [4b472bb6-6ce7-45dc-a33f-79f406456c07]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [149ec0e4-3778-43e3-8723-1274852daad9, 30f24614-b8f5-4f1f-86e3-ade91a5bda96, aec79c21-edd5-4bb6-95cb-3b64a4c2ccc4, f46bc5c5-2449-4fcc-9f86-5f19aaa4ba2e]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4b472bb6-6ce7-45dc-a33f-79f406456c07
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 149ec0e4-3778-43e3-8723-1274852daad9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2cc148e0-095f-4d0d-80a7-8d1a3afa605a]
name                : "eth22"

_uuid               : 30f24614-b8f5-4f1f-86e3-ade91a5bda96
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [25448f6c-3211-4c56-bf0d-e18d2442561d]
name                : "br0"

_uuid               : aec79c21-edd5-4bb6-95cb-3b64a4c2ccc4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8a9a708d-e81c-4534-88af-a4e3964e08e8]
name                : "eth23"

_uuid               : f46bc5c5-2449-4fcc-9f86-5f19aaa4ba2e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8a97455e-ab57-4bf3-9fd9-352cd0adf698]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2cc148e0-095f-4d0d-80a7-8d1a3afa605a
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

_uuid               : 25448f6c-3211-4c56-bf0d-e18d2442561d
admin_state         : down
duplex              : full
ifindex             : 311
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

_uuid               : 8a9a708d-e81c-4534-88af-a4e3964e08e8
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

_uuid               : 8a97455e-ab57-4bf3-9fd9-352cd0adf698
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
commit 42d47927fca08a552c2f28606b664a926663be73
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Thu Jul 30 20:51:15 2015 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Fri Jul 31 19:09:22 2015 -0700

    datapath: Fix STT protocol field for sampling packet.
    
    Fixes typo in STT sampling code.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
