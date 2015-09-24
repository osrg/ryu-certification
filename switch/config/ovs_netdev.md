---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
bc6e0a2e-1064-47ed-bdba-3762cb0f3b2f
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8f252328-d55f-4f0d-9508-e0e026625d22
controller          : [c3f9019b-4742-492a-9639-f55cc75dd36b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [164ea193-f132-40f7-b8d4-f8df0c073c4c, 3033a113-d41c-43ce-905c-9d428448efb3, cd13f273-adeb-49b1-880c-ae97c189ba6b, f1f0775e-c398-4f87-9522-72ba06394884]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c3f9019b-4742-492a-9639-f55cc75dd36b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f1f0775e-c398-4f87-9522-72ba06394884
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [badd0e16-0c0d-40d2-951c-934919477b21]
name                : "eth22"

_uuid               : 164ea193-f132-40f7-b8d4-f8df0c073c4c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [24d05183-7b32-4956-9dae-7e5360130d38]
name                : "eth23"

_uuid               : 3033a113-d41c-43ce-905c-9d428448efb3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [969bd754-708a-4676-944e-66fb420938b2]
name                : "eth21"

_uuid               : cd13f273-adeb-49b1-880c-ae97c189ba6b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a84d7dd8-cca9-4668-9ca5-c7c78dfb80a5]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a84d7dd8-cca9-4668-9ca5-c7c78dfb80a5
admin_state         : down
duplex              : full
ifindex             : 493
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

_uuid               : 969bd754-708a-4676-944e-66fb420938b2
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

_uuid               : badd0e16-0c0d-40d2-951c-934919477b21
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

_uuid               : 24d05183-7b32-4956-9dae-7e5360130d38
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
commit ad4adec2a33fe4edaf0e619ddcbee852c9cbe6a7
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Tue Sep 22 18:13:00 2015 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Wed Sep 23 19:49:27 2015 -0700

    datapath: Backport &quot;openvswitch: Zero flows on allocation.&quot;
    
    Upstream commit:
        openvswitch: Zero flows on allocation.
    
        When support for megaflows was introduced, OVS needed to start
        installing flows with a mask applied to them. Since masking is an
        expensive operation, OVS also had an optimization that would only
        take the parts of the flow keys that were covered by a non-zero
        mask. The values stored in the remaining pieces should not matter
        because they are masked out.
    
        While this works fine for the purposes of matching &#40;which must always
        look at the mask&#41;, serialization to netlink can be problematic. Since
        the flow and the mask are serialized separately, the uninitialized
        portions of the flow can be encoded with whatever values happen to be
        present.
    
        In terms of functionality, this has little effect since these fields
        will be masked out by definition. However, it leaks kernel memory to
        userspace, which is a potential security vulnerability. It is also
        possible that other code paths could look at the masked key and get
        uninitialized data, although this does not currently appear to be an
        issue in practice.
    
        This removes the mask optimization for flows that are being installed.
        This was always intended to be the case as the mask optimizations were
        really targetting per-packet flow operations.
    
        Fixes: 03f0d916 &#40;&quot;openvswitch: Mega flow implementation&quot;&#41;
        Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
        Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
        Signed-off-by: David S. Miller &lt;davem@davemloft.net&gt;
    
    Upstream: ae5f2fb1 &#40;&quot;openvswitch: Zero flows on allocation.&quot;&#41;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
