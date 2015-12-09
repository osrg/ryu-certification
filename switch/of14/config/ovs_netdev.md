---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2891fd40-03ed-46ef-9102-1d9f39dd411a
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
_uuid               : 0ba9a690-9c9f-403d-84bb-0839faf2f720
controller          : [113bd545-4862-435b-b9ac-52aeda4ba510]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2187b4ca-b1fc-4c90-87b8-e51694460475, 7cf6b3b7-4048-44d9-8279-a2ec99e711cc, da8e6e88-de83-4ead-9b40-e3fa4673297c, e8bd648e-82b3-410b-a416-71e966aadf31]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 113bd545-4862-435b-b9ac-52aeda4ba510
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : da8e6e88-de83-4ead-9b40-e3fa4673297c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e8ddcde0-2b35-469f-a499-e1352ee01731]
name                : "eth21"

_uuid               : e8bd648e-82b3-410b-a416-71e966aadf31
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [14f6dff4-e60b-4095-ac96-393d0be964a6]
name                : "br0"

_uuid               : 2187b4ca-b1fc-4c90-87b8-e51694460475
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4424b628-d80b-46f2-aa9e-f58e4af30844]
name                : "eth23"

_uuid               : 7cf6b3b7-4048-44d9-8279-a2ec99e711cc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [57ebc33b-8c4a-473c-b321-e669e46745e9]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e8ddcde0-2b35-469f-a499-e1352ee01731
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
statistics          : {collisions=0, rx_bytes=41927868546, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27999011, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 14f6dff4-e60b-4095-ac96-393d0be964a6
admin_state         : down
duplex              : full
ifindex             : 666
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

_uuid               : 4424b628-d80b-46f2-aa9e-f58e4af30844
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6118108500, tx_dropped=0, tx_errors=0, tx_packets=4078739}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 57ebc33b-8c4a-473c-b321-e669e46745e9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29066488064, tx_dropped=0, tx_errors=0, tx_packets=19398601}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 042852d14cabb1d91fefc9f6ce713796d8459086
Author:     Russell Bryant &lt;russell@ovn.org&gt;
AuthorDate: Tue Dec 8 17:32:47 2015 -0500
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Wed Dec 9 11:17:11 2015 -0500

    ovn: Fix ct_state bit mappings in OVN symtab.
    
    The OVN symbol table contained outdated mappings between connection
    states and the corresponding bit in the ct_state field.  This patch
    updates the symbol table with the proper values as defined in
    lib/packets.h.
    
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
    Fixes: 63bc9fb1c69f &#40;&quot;packets: Reorder CS_* flags to remove gap.&quot;&#41;
    Acked-by: Joe Stringer &lt;joe@ovn.org&gt;
</pre>
