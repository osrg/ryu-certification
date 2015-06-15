---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9c1c9c11-af92-4238-98b6-b866b6e7c12c
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
_uuid               : e64760ec-066e-4dac-ab39-e4924503f1ae
controller          : [8d1d68c6-afb2-4881-b892-b11ea46b42af]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [12dd8554-d934-46fe-87a1-217063e67e8f, 23e00371-3669-4b4b-a805-f028cf64af25, a89951fc-8241-42e6-98ad-5157c6817585, ed7c618a-ae34-4125-80fe-f02e5707036e]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8d1d68c6-afb2-4881-b892-b11ea46b42af
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a89951fc-8241-42e6-98ad-5157c6817585
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [edabde26-a0ac-40f1-9359-a3f20e1b3abd]
name                : "eth21"

_uuid               : 12dd8554-d934-46fe-87a1-217063e67e8f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dcedc65d-ce1c-48ca-ad6f-218b22a1e257]
name                : "eth23"

_uuid               : 23e00371-3669-4b4b-a805-f028cf64af25
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [83faa425-e052-4436-9f35-f688936043f5]
name                : "eth22"

_uuid               : ed7c618a-ae34-4125-80fe-f02e5707036e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1af778d0-ae2d-4550-ace6-995f92f94a9c]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1af778d0-ae2d-4550-ace6-995f92f94a9c
admin_state         : down
duplex              : full
ifindex             : 157
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

_uuid               : dcedc65d-ce1c-48ca-ad6f-218b22a1e257
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

_uuid               : 83faa425-e052-4436-9f35-f688936043f5
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

_uuid               : edabde26-a0ac-40f1-9359-a3f20e1b3abd
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
