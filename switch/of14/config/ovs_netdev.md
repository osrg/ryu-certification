---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e18cd6a6-de07-4749-bdec-50296527819e
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
_uuid               : 267c2323-1d9a-4b00-9347-0dc3a0f6a483
controller          : [5972f730-c749-45d4-bc63-fb9518fe76c7]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [413ffd5a-1cf6-4024-94e1-a1e406e23437, 44054608-9f18-4cb3-94a6-ad9d36214e55, 9f8eb98f-8292-447e-9261-43192a2fd008, ba35f664-9fe0-41d3-a358-f821b11ec08b]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5972f730-c749-45d4-bc63-fb9518fe76c7
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ba35f664-9fe0-41d3-a358-f821b11ec08b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e6e091e8-9f9c-40f1-a7e5-3df606c759d1]
name                : "eth22"

_uuid               : 44054608-9f18-4cb3-94a6-ad9d36214e55
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [608a00a8-a85e-48e9-b4a5-71bf70a7cbde]
name                : "br0"

_uuid               : 413ffd5a-1cf6-4024-94e1-a1e406e23437
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aec6a3b4-a193-498c-a3f3-cf6ae0664d36]
name                : "eth23"

_uuid               : 9f8eb98f-8292-447e-9261-43192a2fd008
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d21f7b17-b21c-4c11-94e4-7974f6e11ade]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e6e091e8-9f9c-40f1-a7e5-3df606c759d1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30488565389, tx_dropped=0, tx_errors=0, tx_packets=20355307}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 608a00a8-a85e-48e9-b4a5-71bf70a7cbde
admin_state         : down
duplex              : full
ifindex             : 770
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

_uuid               : aec6a3b4-a193-498c-a3f3-cf6ae0664d36
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=8486202000, tx_dropped=0, tx_errors=0, tx_packets=5657468}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d21f7b17-b21c-4c11-94e4-7974f6e11ade
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
statistics          : {collisions=0, rx_bytes=45087364587, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30123095, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9aad5a5a96bac423b05b5bb3afb7add2df44bba9
Author:     Ben Pfaff &lt;blp@ovn.org&gt;
AuthorDate: Thu Feb 4 09:48:54 2016 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Fri Feb 5 11:43:35 2016 -0800

    ovs-vswitchd: Preserve datapath ports across graceful shutdown.
    
    Until now, asking ovs-vswitchd to shut down gracefully, e.g. with
    &quot;ovs-appctl exit&quot;, would cause it to first remove all the ports from
    kernel-based datapaths.  This has the unfortunate side effect that IP
    addresses on any removed &quot;internal&quot; ports are lost, even if the ports are
    added again when ovs-vswitchd is restarted.  This is long-standing
    behavior, but it only became important when the OVS control scripts were
    changed to try to do graceful shutdown first instead of using a signal.
    
    This commit changes graceful shutdown so that it leaves ports in the
    datapath, fixing the problem.
    
    Fixes: 9b5422a98f8 &#40;ovs-lib: Try to call exit before killing.&#41;
    Reported-by: Edgar Cantu &lt;eocantu@us.ibm.com&gt;
    Reported-at: http://openvswitch.org/pipermail/discuss/2016-January/020024.html
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
    Acked-by: Gurucharan Shetty &lt;guru@ovn.org&gt;
</pre>
