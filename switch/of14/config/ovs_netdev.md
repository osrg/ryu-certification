---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
45f74a44-3a27-4e45-b59b-2a7f783fc7c1
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 1fcdd4c4-b036-40e2-ba5b-b8c3bfcb133d
controller          : [2d389db7-b988-41bf-99bb-464d67fe38f1]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [d31ff384-8c3a-4594-9de2-f505d63ab57e, e96f16d5-ac99-4612-b758-7fe82f03010a, f1cdc4ce-dfb3-40c4-9270-a03647c8f4e0, f5bbb85d-c93f-4b9a-a2e2-cad718dac96b]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2d389db7-b988-41bf-99bb-464d67fe38f1
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="762", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d31ff384-8c3a-4594-9de2-f505d63ab57e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4c172290-5df3-4ee6-b8f3-9e25948af4a7]
name                : "eth21"

_uuid               : f5bbb85d-c93f-4b9a-a2e2-cad718dac96b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a9184837-2d25-4e5b-a25c-acab68e4050c]
name                : "eth23"

_uuid               : e96f16d5-ac99-4612-b758-7fe82f03010a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ebf3d703-c5e5-478e-84b1-2d31793ed435]
name                : "br0"

_uuid               : f1cdc4ce-dfb3-40c4-9270-a03647c8f4e0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4d6d8d1e-1467-4016-b5a1-6eccc8148598]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4c172290-5df3-4ee6-b8f3-9e25948af4a7
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
statistics          : {collisions=0, rx_bytes=37960955327, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=25332610, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 4d6d8d1e-1467-4016-b5a1-6eccc8148598
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=27243997654, tx_dropped=0, tx_errors=0, tx_packets=18173917}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a9184837-2d25-4e5b-a25c-acab68e4050c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3181810500, tx_dropped=0, tx_errors=0, tx_packets=2121207}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ebf3d703-c5e5-478e-84b1-2d31793ed435
admin_state         : down
duplex              : full
ifindex             : 569
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
commit 38b366b1c3f5ca3f8b96782af6432f77c48cb2c9
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Thu Oct 15 09:19:11 2015 -0700
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Thu Oct 15 09:22:17 2015 -0700

    vswitch.xml: Add caveat to flow-limit.
    
    This option should only be tweaked by developers investigating the
    behaviour of flow caching, so recommend that this option is not used.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
