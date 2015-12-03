---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8b9348f3-357d-4358-9965-f110b5123f78
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 22f19fea-31d1-4af9-ad96-dd2a4e843f2d
controller          : [cb1508fd-3d50-4d5f-888d-e67761c09b22]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [4af8a87a-34b0-423f-bfe7-6e4e1b5f16d5, 582e2f31-36c7-4680-86a1-55d28c3d251f, 830ad9b0-5888-4f43-8796-dd558cc9fd8b, a1dad8e1-5a5a-486a-a54a-220a777bcab0]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : cb1508fd-3d50-4d5f-888d-e67761c09b22
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 830ad9b0-5888-4f43-8796-dd558cc9fd8b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4d123a81-9bd5-4ea5-ad4c-a55ab77125d5]
name                : "br0"

_uuid               : a1dad8e1-5a5a-486a-a54a-220a777bcab0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8b90d8b5-aa4c-4d3b-8063-265f392941f3]
name                : "eth22"

_uuid               : 582e2f31-36c7-4680-86a1-55d28c3d251f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [33857ed4-fba3-42e5-8ca7-ab465d7a304b]
name                : "eth23"

_uuid               : 4af8a87a-34b0-423f-bfe7-6e4e1b5f16d5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b834005e-1f64-457f-b064-403871fd57d7]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 33857ed4-fba3-42e5-8ca7-ab465d7a304b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5679474000, tx_dropped=0, tx_errors=0, tx_packets=3786316}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 8b90d8b5-aa4c-4d3b-8063-265f392941f3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28803225391, tx_dropped=0, tx_errors=0, tx_packets=19221486}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 4d123a81-9bd5-4ea5-ad4c-a55ab77125d5
admin_state         : down
duplex              : full
ifindex             : 644
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

_uuid               : b834005e-1f64-457f-b064-403871fd57d7
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
statistics          : {collisions=0, rx_bytes=41342767333, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27605652, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1b43cf9e68f4dd0dab4f9d3fa9dd80aeb642c139
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Tue Dec 1 16:17:46 2015 -0800
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Thu Dec 3 09:54:37 2015 -0800

    ofproto-dpif: Validate ct action support.
    
    Disallow installing rules that execute ct&#40;&#41; if conntrack is unsupported
    in the datapath.
    
    Reported-by: Ravindra Kenchappa &lt;ravindra.kenchappa@hpe.com&gt;
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jarno@ovn.org&gt;
</pre>
