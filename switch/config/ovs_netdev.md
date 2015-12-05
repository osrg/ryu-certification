---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9755269b-5daa-4805-9dad-109128f0a0af
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0aa9ad50-90d2-4ba5-ba55-f638a65bbca4
controller          : [13e93168-7750-4429-a96e-dadff601d05e]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [37e511a4-6857-4d7b-b249-47eefe866229, 472e1f7d-e62c-438c-9daa-16971cef7c5c, a3fdaab1-7be2-45ab-9369-82f36e425e95, c32239bc-6862-4354-86e6-da922460e667]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 13e93168-7750-4429-a96e-dadff601d05e
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c32239bc-6862-4354-86e6-da922460e667
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4b25b03a-8fde-4b84-9399-46483d330883]
name                : "eth22"

_uuid               : 37e511a4-6857-4d7b-b249-47eefe866229
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c155def4-1e19-4ff6-91c2-b2e17b0eb54a]
name                : "eth21"

_uuid               : 472e1f7d-e62c-438c-9daa-16971cef7c5c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [caad7a75-fff9-4328-bb80-55043ed2beb0]
name                : "br0"

_uuid               : a3fdaab1-7be2-45ab-9369-82f36e425e95
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f04d4930-29c9-48c0-bc92-2fba4814de35]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f04d4930-29c9-48c0-bc92-2fba4814de35
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5854765500, tx_dropped=0, tx_errors=0, tx_packets=3903177}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c155def4-1e19-4ff6-91c2-b2e17b0eb54a
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
statistics          : {collisions=0, rx_bytes=41576817615, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27763001, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : caad7a75-fff9-4328-bb80-55043ed2beb0
admin_state         : down
duplex              : full
ifindex             : 652
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

_uuid               : 4b25b03a-8fde-4b84-9399-46483d330883
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28908700157, tx_dropped=0, tx_errors=0, tx_packets=19292444}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7b27258c4e0821ade73e0e0a9bd5339328489523
Author:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
AuthorDate: Fri Dec 4 15:01:37 2015 -0800
Commit:     Jarno Rajahalme &lt;jarno@ovn.org&gt;
CommitDate: Fri Dec 4 15:01:37 2015 -0800

    ofproto-dpif: Validate NAT action support.
    
    The NAT validation is similar &#40;and based on&#41; the existing conntrack
    validation: when a dpif backer is created, we try to install a flow with
    the ct_state NAT bits set.  If the flow setup fails we assume that the
    backer doesn't support NAT and we reject OpenFlow flows with a NAT
    action or a match on the ct_state NAT bits.
    
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>
