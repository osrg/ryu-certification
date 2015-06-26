---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d9c2e0e7-231d-4b3f-8ab6-ad245c728076
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
_uuid               : 4569cfd8-2148-4631-b8b6-37340b927042
controller          : [b43726fe-ac15-4341-ad90-e68cba5ece9e]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [14aacb94-d99e-4108-8d83-5a78f63613fb, aac95dae-39ef-44b8-8adf-026ebffadb87, d059613e-a9b5-4d1a-b466-eafe13f8faf0, eb28edf9-d09a-4686-b394-a49f1d0f353c]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b43726fe-ac15-4341-ad90-e68cba5ece9e
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 14aacb94-d99e-4108-8d83-5a78f63613fb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8853ae51-0e96-4d7d-badf-b6e0a0553187]
name                : "eth21"

_uuid               : eb28edf9-d09a-4686-b394-a49f1d0f353c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b688a678-f7bb-484b-8ee9-74a607908ce6]
name                : "eth23"

_uuid               : aac95dae-39ef-44b8-8adf-026ebffadb87
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0299ec86-f3c3-49f5-882c-66df7c51ec67]
name                : "br0"

_uuid               : d059613e-a9b5-4d1a-b466-eafe13f8faf0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c386f99a-0654-4ae6-9ae3-a6ebe3045a5a]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b688a678-f7bb-484b-8ee9-74a607908ce6
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

_uuid               : 8853ae51-0e96-4d7d-badf-b6e0a0553187
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

_uuid               : c386f99a-0654-4ae6-9ae3-a6ebe3045a5a
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

_uuid               : 0299ec86-f3c3-49f5-882c-66df7c51ec67
admin_state         : down
duplex              : full
ifindex             : 200
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
commit daab0ae6bb558411f24cee6a7bb32599a5f9e363
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Jun 23 11:38:56 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Jun 26 08:44:20 2015 -0700

    ofproto: Fix use-after-free in bridge destruction with groups.
    
    Groups were not destroyed until after lots of other important bridge
    data had been destroyed, including the connection manager.  There was an
    indirect dependency on the connection manager for bridge destruction
    because destroying a group also destroys all of the flows that reference
    the group, which in turn causes the ofmonitor to be invoked to report that
    the flows had been destroyed.  This commit fixes the problem by destroying
    groups earlier.
    
    The problem can be observed by reverting the code changes in this commit
    then running &quot;make check-valgrind&quot; with the test that this commit
    introduces.
    
    Reported-by: Simon Horman &lt;simon.horman@netronome.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Reviewed-by: Simon Horman &lt;simon.horman@netronome.com&gt;
</pre>
