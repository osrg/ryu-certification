---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c2511c1a-5815-4eb7-8258-99ef6adee93f
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 3fdb5765-1f4b-459d-88d1-438660ec4da8
controller          : [808a7e8b-3d43-4e63-8ae9-c40f9acc1c45]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0895933f-d251-4287-8437-5e74793d4421, 121d3e45-14ff-43ea-959a-4ddcb363222c, 495c57bc-0559-4af3-a691-0ee590ae07ca, 975d3e84-c0f3-49b9-8bb9-fd5994f94ac3]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 808a7e8b-3d43-4e63-8ae9-c40f9acc1c45
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 975d3e84-c0f3-49b9-8bb9-fd5994f94ac3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [913310a7-2e11-49e0-90c9-5c4707e554a2]
name                : "eth22"

_uuid               : 495c57bc-0559-4af3-a691-0ee590ae07ca
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3f3000f5-e3dc-41d4-af49-63c0a62bc56e]
name                : "eth23"

_uuid               : 121d3e45-14ff-43ea-959a-4ddcb363222c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [43647b3a-9048-42a0-b20b-b2cf830c4a85]
name                : "eth21"

_uuid               : 0895933f-d251-4287-8437-5e74793d4421
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [095eacfa-cd48-45a2-b6c4-4a37426c0ebd]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3f3000f5-e3dc-41d4-af49-63c0a62bc56e
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

_uuid               : 43647b3a-9048-42a0-b20b-b2cf830c4a85
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

_uuid               : 095eacfa-cd48-45a2-b6c4-4a37426c0ebd
admin_state         : down
duplex              : full
ifindex             : 435
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

_uuid               : 913310a7-2e11-49e0-90c9-5c4707e554a2
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
commit ca92d173aa29240c38735ad9e4f46e4222792b52
Author:     Aaron Conole &lt;aconole@redhat.com&gt;
AuthorDate: Fri Sep 4 16:53:30 2015 -0400
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Sat Sep 5 19:45:56 2015 -0700

    netdev-dpdk: Fix build failure due to new struct eth_addr.
    
    The netdev-dpdk uses the struct ether_addr rather than struct eth_addr
    internal ovs datatype.
    
    To facilitate using either the .ea OR the struct ether_addr.addr_bytes
    argument for printing/logging, add a new ETH_ADDR_BYTES_ARG&#40;&#41; define.
    
    Signed-off-by: Aaron Conole &lt;aconole@redhat.com&gt;
    [blp@nicira.com made stylistic changes]
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
