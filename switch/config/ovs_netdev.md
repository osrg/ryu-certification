---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0134780b-45e8-4ac2-994b-50cc14676ed9
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
_uuid               : 0b79beec-9e99-4d74-9223-258141e595b8
controller          : [e1b90af4-390d-4b7a-90e0-d68b176ff2d2]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [22ba9d51-59df-4761-9255-9fe638621569, ae355ed8-f498-475b-a7a6-ad4c577e8467, c0fc5401-7983-40d6-80fd-05c72a4c562b, f32243e2-6358-45e9-a407-4309640d8622]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e1b90af4-390d-4b7a-90e0-d68b176ff2d2
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ae355ed8-f498-475b-a7a6-ad4c577e8467
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f409b884-a610-4ac6-a748-12f2414922b7]
name                : "eth22"

_uuid               : c0fc5401-7983-40d6-80fd-05c72a4c562b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2f15914c-42e9-40e3-8f90-1423c88d1262]
name                : "br0"

_uuid               : 22ba9d51-59df-4761-9255-9fe638621569
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [05f01f29-a942-4645-acb1-f47eb00b8a4d]
name                : "eth21"

_uuid               : f32243e2-6358-45e9-a407-4309640d8622
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b57f7c78-a104-4109-92be-4645eee36475]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2f15914c-42e9-40e3-8f90-1423c88d1262
admin_state         : down
duplex              : full
ifindex             : 826
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

_uuid               : b57f7c78-a104-4109-92be-4645eee36475
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9801657000, tx_dropped=0, tx_errors=0, tx_packets=6534438}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f409b884-a610-4ac6-a748-12f2414922b7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31278706118, tx_dropped=0, tx_errors=0, tx_packets=20886873}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 05f01f29-a942-4645-acb1-f47eb00b8a4d
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
statistics          : {collisions=0, rx_bytes=46842581436, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31303100, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1478295a219f24c2296eb887954afac537c3665f
Author:     Ilya Maximets &lt;i.maximets@samsung.com&gt;
AuthorDate: Wed Feb 24 18:04:57 2016 +0300
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Wed Feb 24 10:18:19 2016 -0500

    configure: Fix checking of six library for Python 3.
    
    Copied from python 2 checker but not corrected.
    
    Fixes: 8fb7d02686ed &#40;&quot;configure: Check for presence of Python 3.&quot;&#41;
    Signed-off-by: Ilya Maximets &lt;i.maximets@samsung.com&gt;
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
</pre>
