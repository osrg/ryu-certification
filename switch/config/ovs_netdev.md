---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1eef58fe-6f54-43e2-a06e-e9f2aa8763a0
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
_uuid               : 191a5a7d-aac1-4976-b7fb-d58d11ca6ddb
controller          : [1a9625c2-67ae-469d-9a5c-a848a34af456]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0a207e1a-8920-435b-9dcd-11dca4aa54ec, 28234377-8543-42ec-b688-c12333839b19, 49b141fb-5541-4547-9008-ce0897a317a4, 8ab3113f-667b-49bf-bc30-2732c01014b4]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 1a9625c2-67ae-469d-9a5c-a848a34af456
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0a207e1a-8920-435b-9dcd-11dca4aa54ec
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [48ba3d12-ba3c-4b75-84ea-723c82fecca8]
name                : "br0"

_uuid               : 49b141fb-5541-4547-9008-ce0897a317a4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ffadd805-de0d-4e83-8edd-093f7f78ae2b]
name                : "eth23"

_uuid               : 28234377-8543-42ec-b688-c12333839b19
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0cba9f20-eb66-46f1-a9bb-a2452eff4ae0]
name                : "eth22"

_uuid               : 8ab3113f-667b-49bf-bc30-2732c01014b4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7aea0acf-d477-438b-8033-24e2993b3653]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0cba9f20-eb66-46f1-a9bb-a2452eff4ae0
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

_uuid               : ffadd805-de0d-4e83-8edd-093f7f78ae2b
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

_uuid               : 48ba3d12-ba3c-4b75-84ea-723c82fecca8
admin_state         : down
duplex              : full
ifindex             : 208
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

_uuid               : 7aea0acf-d477-438b-8033-24e2993b3653
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
commit bc651c85497d7a8c32e83b44986dae27dec3bcd5
Author:     Sorin Vinturis &lt;svinturis@cloudbasesolutions.com&gt;
AuthorDate: Wed Jul 1 15:32:18 2015 +0000
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jul 1 10:20:35 2015 -0700

    datapath-windows: Failed initialization for datapath tunnel ports
    
    Tunnel ports are not initialized with the corresponding default port.
    The newly allocated vport is not yet initialized and the ovsType
    member does not reflect the correct tunnel port type, thus the
    transport port destination won't be correctly initialized.
    
    Signed-off-by: Sorin Vinturis &lt;svinturis@cloudbasesolutions.com&gt;
    Reported-by: Sorin Vinturis &lt;svinturis@cloudbasesolutions.com&gt;
    Reported-at: https://github.com/openvswitch/ovs-issues/issues/88
    Acked-by: Eitan Eliahu &lt;eliahue@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
