---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7d425646-9b18-41bf-8f1c-53e7558c50e5
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
_uuid               : 2bb1834b-92ca-4c3d-8d07-bc8655d15f6c
controller          : [8c6ab3cd-019d-4256-8933-4276ffa5b52a]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3aadf77f-b488-4a71-9f2a-236c4473784e, 6334c4c4-0a02-4999-a5e7-ee29e410b073, bcfb8d6e-040e-4cb5-a17f-c9d20770c982, d97076f2-774d-4f3c-95d4-ff41d46ace25]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8c6ab3cd-019d-4256-8933-4276ffa5b52a
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6334c4c4-0a02-4999-a5e7-ee29e410b073
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b5215ecf-959e-430c-a324-e8ce4be9ceaf]
name                : "eth22"

_uuid               : d97076f2-774d-4f3c-95d4-ff41d46ace25
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [822647ec-929e-4a14-a863-6804432824c9]
name                : "eth21"

_uuid               : bcfb8d6e-040e-4cb5-a17f-c9d20770c982
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [32dabb1b-bf98-43ee-957c-f0ac81ab7dc0]
name                : "eth23"

_uuid               : 3aadf77f-b488-4a71-9f2a-236c4473784e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [74244d01-77b8-4989-8b00-d79bd7a3f067]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 822647ec-929e-4a14-a863-6804432824c9
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
statistics          : {collisions=0, rx_bytes=43800178786, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29257736, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 74244d01-77b8-4989-8b00-d79bd7a3f067
admin_state         : down
duplex              : full
ifindex             : 726
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

_uuid               : b5215ecf-959e-430c-a324-e8ce4be9ceaf
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29908979176, tx_dropped=0, tx_errors=0, tx_packets=19965388}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 32dabb1b-bf98-43ee-957c-f0ac81ab7dc0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7521670500, tx_dropped=0, tx_errors=0, tx_packets=5014447}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 03756304cf67a4f241ea124696ab0dbf40d9d679
Author:     Russell Bryant &lt;russell@ovn.org&gt;
AuthorDate: Wed Jan 6 15:23:08 2016 -0500
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Fri Jan 22 08:25:27 2016 -0500

    python: Remove old style classes.
    
    Python 3 removed support for &quot;old-style classes&quot;.  Classes should always
    inherit from object to get consistent behavior between Python 2 and 3.
    
    Enable a flake8 warning to help prevent regressions in the future.
    
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
