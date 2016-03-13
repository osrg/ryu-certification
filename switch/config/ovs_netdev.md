---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fb37d04e-b5ae-41e0-9dd0-5bf97945af10
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
_uuid               : 06c958ba-1264-44d5-8944-6ca854262d75
controller          : [3ea9766b-7228-41d5-9c80-00699bd87459]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2dd8070d-f160-462d-a006-8e56555196f4, 557c46bd-54b1-4395-bcbb-213e8e5c1511, 880c8bfe-69fb-4b4a-a137-f094f3c1c809, d75340cf-639b-4947-9467-0702d5d85219]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3ea9766b-7228-41d5-9c80-00699bd87459
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="672", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 557c46bd-54b1-4395-bcbb-213e8e5c1511
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0596f53d-9dfa-47ae-98c8-3d6f03b37d7a]
name                : "eth22"

_uuid               : 2dd8070d-f160-462d-a006-8e56555196f4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d28166f4-6544-4e69-be9b-87a5153e7e32]
name                : "eth21"

_uuid               : 880c8bfe-69fb-4b4a-a137-f094f3c1c809
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9a97b199-4481-466f-91da-202bd896559b]
name                : "br0"

_uuid               : d75340cf-639b-4947-9467-0702d5d85219
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c3732fdf-21ca-4987-aa7f-02c8a4369b65]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d28166f4-6544-4e69-be9b-87a5153e7e32
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
statistics          : {collisions=0, rx_bytes=48246796386, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=32247139, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 0596f53d-9dfa-47ae-98c8-3d6f03b37d7a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31911205472, tx_dropped=0, tx_errors=0, tx_packets=21312391}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9a97b199-4481-466f-91da-202bd896559b
admin_state         : down
duplex              : full
ifindex             : 876
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

_uuid               : c3732fdf-21ca-4987-aa7f-02c8a4369b65
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
