---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fb854e31-977f-46ab-a570-4d37b1e13f48
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 4602b177-c1b3-466c-ada3-b712e9b6a6b0
controller          : [29b82583-27c4-4291-bf19-6314f468b803]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0306f259-9446-4d0b-acec-f3844c9197cf, 1d7682ed-9ef4-4038-ab2f-5f08ac0ef4ce, c44f526c-4f7a-45f2-aec8-2be0ad74c601, f30c22e0-5736-4534-91b7-dbedd9e0b82d]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 29b82583-27c4-4291-bf19-6314f468b803
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c44f526c-4f7a-45f2-aec8-2be0ad74c601
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0128d446-96a1-485b-82d3-6cc0748685ae]
name                : "eth21"

_uuid               : f30c22e0-5736-4534-91b7-dbedd9e0b82d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [90a26a50-9f26-4b6a-a3e3-01418bbde9b0]
name                : "br0"

_uuid               : 0306f259-9446-4d0b-acec-f3844c9197cf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [56f1dd80-2d9e-432d-90e9-8df52a2fceae]
name                : "eth22"

_uuid               : 1d7682ed-9ef4-4038-ab2f-5f08ac0ef4ce
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bb971596-9685-4d80-878b-7e6e5d6e7480]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 56f1dd80-2d9e-432d-90e9-8df52a2fceae
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

_uuid               : 90a26a50-9f26-4b6a-a3e3-01418bbde9b0
admin_state         : down
duplex              : full
ifindex             : 433
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

_uuid               : 0128d446-96a1-485b-82d3-6cc0748685ae
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

_uuid               : bb971596-9685-4d80-878b-7e6e5d6e7480
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
