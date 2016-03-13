---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
dfed153f-9782-47a0-a0cc-d8482f83008b
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : dec7987f-9eae-4f9b-9aae-111d4861e1c2
controller          : [209a1647-2893-4077-a385-a1849d3d3327]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [19d07d15-4844-44fd-9a07-e455bd300f33, 54603bce-da22-421f-b964-544558b11dfe, 8d1224f9-bb9e-4591-bdbf-6b03c471621a, aab67484-f6da-4cbd-8be8-bd8a2be0ebd0]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 209a1647-2893-4077-a385-a1849d3d3327
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="16", sec_since_disconnect="4", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : aab67484-f6da-4cbd-8be8-bd8a2be0ebd0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [25141293-1868-47af-be4f-e6257ecee870]
name                : "eth21"

_uuid               : 19d07d15-4844-44fd-9a07-e455bd300f33
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1a794d1a-4012-4eeb-bf14-a9e01043dfef]
name                : "br0"

_uuid               : 8d1224f9-bb9e-4591-bdbf-6b03c471621a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [168f77cb-8217-4285-a88c-268886e5878e]
name                : "eth23"

_uuid               : 54603bce-da22-421f-b964-544558b11dfe
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [375bb114-f45e-4654-86ce-2489a616d413]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 375bb114-f45e-4654-86ce-2489a616d413
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31911205730, tx_dropped=0, tx_errors=0, tx_packets=21312394}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1a794d1a-4012-4eeb-bf14-a9e01043dfef
admin_state         : down
duplex              : full
ifindex             : 878
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

_uuid               : 25141293-1868-47af-be4f-e6257ecee870
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
statistics          : {collisions=0, rx_bytes=48246796644, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=32247142, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 168f77cb-8217-4285-a88c-268886e5878e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10853665500, tx_dropped=0, tx_errors=0, tx_packets=7235777}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0bac7164d727898492c54ab54f7e745a1d963e1e
Author:     Ben Pfaff &lt;blp@ovn.org&gt;
AuthorDate: Fri Feb 19 16:34:19 2016 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Sat Mar 12 14:06:43 2016 -0800

    ovn: Implement basic ARP support for L3 logical routers.
    
    This is sufficient support that an L3 logical router can now transmit
    packets to VMs &#40;and other destinations&#41; without having to know the
    IP-to-MAC binding in advance.  The details are carefully documented in all
    of the appropriate places.
    
    There are several important caveats that need to be fixed before this can
    be taken seriously in production.  These are documented in ovn/TODO.  The
    most important of these are renewal, expiration, and limiting the size of
    the ARP table.
    
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
    Acked-by: Justin Pettit &lt;jpettit@ovn.org&gt;
</pre>
