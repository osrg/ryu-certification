---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0ea31736-bbde-4f7a-b597-fa61306b0d13
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 707e8001-e079-4183-bbbd-70798fde20d9
controller          : [37cbcd9b-e75a-455b-9d1e-37d9d6a37f1a]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [02716a26-5ceb-42c7-992e-9ba2eaccecce, 30e62e61-7a14-419e-870e-991f142ff15c, 6a832ac3-5ad0-4a55-95a6-5541d19761bb, b5e2b122-cc8c-42c0-8569-f31dc61cee61]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 37cbcd9b-e75a-455b-9d1e-37d9d6a37f1a
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 30e62e61-7a14-419e-870e-991f142ff15c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [21d942ef-e2b6-49ab-8845-52e3ac785a15]
name                : "eth22"

_uuid               : 02716a26-5ceb-42c7-992e-9ba2eaccecce
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [eb1c9230-950d-4a35-85fa-e00583a8e67b]
name                : "eth21"

_uuid               : b5e2b122-cc8c-42c0-8569-f31dc61cee61
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [932e23e7-a8a2-4731-aa22-f3b85d80d1e6]
name                : "br0"

_uuid               : 6a832ac3-5ad0-4a55-95a6-5541d19761bb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6ebaa848-61c4-4fe1-97eb-34d75971f531]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6ebaa848-61c4-4fe1-97eb-34d75971f531
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

_uuid               : eb1c9230-950d-4a35-85fa-e00583a8e67b
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
statistics          : {collisions=0, rx_bytes=41927868288, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27999008, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 932e23e7-a8a2-4731-aa22-f3b85d80d1e6
admin_state         : down
duplex              : full
ifindex             : 664
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

_uuid               : 21d942ef-e2b6-49ab-8845-52e3ac785a15
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29066487806, tx_dropped=0, tx_errors=0, tx_packets=19398598}
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
