---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b6f1198f-d484-4dfe-a74c-ac3111838286
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 89f5bf20-f5b4-46ec-b088-1256e041af3e
controller          : [b0dc4fc2-e131-49d5-8e24-8dece17c0815]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [26bdd2b8-8814-43ea-96d3-f66e7a87c959, 721da926-22d3-4313-9b05-10bdcb95d566, 9e1dd6c6-58a6-4a8f-8468-710a7aaf4c3a, ac2b2fb1-8875-46eb-a479-af0f64eb22a0]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b0dc4fc2-e131-49d5-8e24-8dece17c0815
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="11", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 26bdd2b8-8814-43ea-96d3-f66e7a87c959
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3b321089-317b-43d0-9f5f-4b2a3a2f4b5d]
name                : "eth23"

_uuid               : ac2b2fb1-8875-46eb-a479-af0f64eb22a0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d2f2bd52-d097-44a5-814f-cf72f2fbca07]
name                : "eth22"

_uuid               : 721da926-22d3-4313-9b05-10bdcb95d566
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [248037c9-d801-4474-b10e-c8e6b59758bf]
name                : "br0"

_uuid               : 9e1dd6c6-58a6-4a8f-8468-710a7aaf4c3a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b366d5e3-4e3d-47c4-877e-6bcda77cce86]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3b321089-317b-43d0-9f5f-4b2a3a2f4b5d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10327834500, tx_dropped=0, tx_errors=0, tx_packets=6885223}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 248037c9-d801-4474-b10e-c8e6b59758bf
admin_state         : down
duplex              : full
ifindex             : 854
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

_uuid               : d2f2bd52-d097-44a5-814f-cf72f2fbca07
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31594766432, tx_dropped=0, tx_errors=0, tx_packets=21099510}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b366d5e3-4e3d-47c4-877e-6bcda77cce86
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
statistics          : {collisions=0, rx_bytes=47544680298, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31775118, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3a103e4a99d1d66344277473a5618c34321a59a0
Author:     Russell Bryant &lt;russell@ovn.org&gt;
AuthorDate: Thu Mar 3 10:15:14 2016 -0500
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Thu Mar 3 12:37:34 2016 -0500

    ovs-ofctl.8: commit is required with alg in ct&#40;&#41;.
    
    The &quot;alg=&quot; argument to the ct&#40;&#41; action only makes sense when used in
    combination with &quot;commit&quot;.  Add this to the documentation to help make
    it clear.
    
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
    Acked-by: Justin Pettit &lt;jpettit@ovn.org&gt;
</pre>
