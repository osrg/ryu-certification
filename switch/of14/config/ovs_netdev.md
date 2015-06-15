---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
edfcaafb-1ac2-42a0-9b66-e9e4cb250328
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
_uuid               : fcb4844f-8539-4be9-8282-cea003d8f712
controller          : [e65812ad-e1e6-47a0-958d-040dada8d6f8]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [58d0c1df-b522-40e5-97bd-cc23deaec5fb, 6be0491e-c55c-4e87-acd6-42d3d9910ea5, 7228b8f0-deb5-49a8-b0bf-22b76fe417de, 8b5a4583-8a6b-46bd-966a-947929334ab4]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e65812ad-e1e6-47a0-958d-040dada8d6f8
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7228b8f0-deb5-49a8-b0bf-22b76fe417de
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [74dfa462-c8b3-4131-8404-7d705ec03e75]
name                : "br0"

_uuid               : 6be0491e-c55c-4e87-acd6-42d3d9910ea5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [04b581c9-1a31-4f53-aaa1-14b9a7c32acc]
name                : "eth23"

_uuid               : 58d0c1df-b522-40e5-97bd-cc23deaec5fb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1eceeca7-2b7a-46ea-bec3-a2624af3bafa]
name                : "eth21"

_uuid               : 8b5a4583-8a6b-46bd-966a-947929334ab4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [17a6d7c6-3e9a-4513-a075-b545cf24cd22]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 04b581c9-1a31-4f53-aaa1-14b9a7c32acc
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

_uuid               : 17a6d7c6-3e9a-4513-a075-b545cf24cd22
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

_uuid               : 74dfa462-c8b3-4131-8404-7d705ec03e75
admin_state         : down
duplex              : full
ifindex             : 159
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

_uuid               : 1eceeca7-2b7a-46ea-bec3-a2624af3bafa
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
commit 7d1ced01772de541d6692c7d5604210e274bcd37
Author:     Ciara Loftus &lt;ciara.loftus@intel.com&gt;
AuthorDate: Thu Jun 4 06:51:40 2015 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Sun Jun 14 20:36:52 2015 -0700

    netdev-dpdk: add dpdk vhost-user ports
    
    This patch adds support for a new port type to the userspace
    datapath called dpdkvhostuser.
    
    A new dpdkvhostuser port will create a unix domain socket which
    when provided to QEMU is used to facilitate communication between
    the virtio-net device on the VM and the OVS port on the host.
    
    vhost-cuse &#40;'dpdkvhost'&#41; ports are still available as 'dpdkvhostcuse'
    ports and will be enabled if vhost-cuse support is detected in the
    DPDK build specified during compilation of the switch. Otherwise,
    vhost-user ports are enabled.
    
    Signed-off-by: Ciara Loftus &lt;ciara.loftus@intel.com&gt;
    Acked-by: Flavio Leitner &lt;fbl@redhat.com&gt;
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
