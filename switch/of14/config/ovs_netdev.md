---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ffa1b510-dbd6-47be-9c3f-61c50ff23120
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
_uuid               : f1927112-281b-4e54-9110-577057224b52
controller          : [e1af32d9-3e99-475d-bb85-021aaf6e9220]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0594fe45-91a6-4b1f-b7b1-f3fc95526329, a3cbc871-7945-4d91-bea5-92b17b89936e, c29200c9-9dc9-40b2-919c-6a22ade9b37b, ddb5617a-e6d5-4770-a012-02ec73d437d2]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e1af32d9-3e99-475d-bb85-021aaf6e9220
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c29200c9-9dc9-40b2-919c-6a22ade9b37b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a8325ef3-c3fa-461c-aadf-7953dd72c006]
name                : "br0"

_uuid               : a3cbc871-7945-4d91-bea5-92b17b89936e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [75f3681a-067e-4521-bf97-a14d744dc6a1]
name                : "eth23"

_uuid               : 0594fe45-91a6-4b1f-b7b1-f3fc95526329
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [95a61bca-fbaa-41d0-8228-19db33d1570b]
name                : "eth21"

_uuid               : ddb5617a-e6d5-4770-a012-02ec73d437d2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b0f06712-2c61-4c2d-bfef-971e6331495d]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b0f06712-2c61-4c2d-bfef-971e6331495d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29171902830, tx_dropped=0, tx_errors=0, tx_packets=19469519}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 95a61bca-fbaa-41d0-8228-19db33d1570b
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
statistics          : {collisions=0, rx_bytes=42161908328, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28156353, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 75f3681a-067e-4521-bf97-a14d744dc6a1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6293452500, tx_dropped=0, tx_errors=0, tx_packets=4195635}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a8325ef3-c3fa-461c-aadf-7953dd72c006
admin_state         : down
duplex              : full
ifindex             : 674
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
commit 3819692e6df7607eb94af8fd29a2976a1fc728ad
Author:     Sairam Venugopal &lt;vsairam@vmware.com&gt;
AuthorDate: Wed Dec 9 17:31:03 2015 -0800
Commit:     Justin Pettit &lt;jpettit@ovn.org&gt;
CommitDate: Fri Dec 11 12:39:21 2015 -0800

    datapath-windows: Fix compilation issue
    
    The previous patch was missing a &quot;;&quot;.
    
    Signed-off-by: Sairam Venugopal &lt;vsairam@vmware.com&gt;
    Acked-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Signed-off-by: Justin Pettit &lt;jpettit@ovn.org&gt;
</pre>
