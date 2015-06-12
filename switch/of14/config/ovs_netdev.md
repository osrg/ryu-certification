---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
488bc923-8970-43ae-9516-34b3210108b7
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ee743898-77bb-4194-b267-8e48a4fc3815
controller          : [f027e0cb-4b28-40ad-ad9e-313074ac8654]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0eaaea68-f07d-4b87-9f84-02291c89b9c2, 176d48f4-cdfc-43d1-9c2a-d6d04473f763, 531ea154-0e99-4b82-bfbe-a8721731cf3d, a1a639ce-0dc9-41ca-94ef-92262e179b42]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f027e0cb-4b28-40ad-ad9e-313074ac8654
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0eaaea68-f07d-4b87-9f84-02291c89b9c2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [79540df9-00d3-4ed3-ba71-845a3084c788]
name                : "eth23"

_uuid               : 531ea154-0e99-4b82-bfbe-a8721731cf3d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [862e01eb-6a2e-4eb3-a9af-c95af1ba4c16]
name                : "eth22"

_uuid               : 176d48f4-cdfc-43d1-9c2a-d6d04473f763
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [98b0991b-256c-45ab-a213-69c26c022d88]
name                : "br0"

_uuid               : a1a639ce-0dc9-41ca-94ef-92262e179b42
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [86eb3138-eff9-4b1d-80f2-8626702fa9f3]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 86eb3138-eff9-4b1d-80f2-8626702fa9f3
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

_uuid               : 79540df9-00d3-4ed3-ba71-845a3084c788
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

_uuid               : 98b0991b-256c-45ab-a213-69c26c022d88
admin_state         : down
duplex              : full
ifindex             : 151
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

_uuid               : 862e01eb-6a2e-4eb3-a9af-c95af1ba4c16
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 2541d75983cb6a48f0303ab96ec2a1be1b0ccbe7
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Thu Jun 11 17:28:37 2015 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Thu Jun 11 17:28:37 2015 -0700

    rculist: Remove postponed poisoning.
    
    Postponed 'next' member poisoning was based on the faulty assumption
    that postponed functions would be called in the order they were
    postponed.  This assumption holds only for the functions postponed by
    any single thread.  When functions are postponed by different
    threads, there are no guarantees of the order in which the functions
    may be called, or timing between those calls after the next grace
    period has passed.
    
    Given this, the postponed poisoning could have executed after
    postponed destruction of the object containing the rculist element.
    
    This bug was revealed after the memory leaks on rule deletion were
    recently fixed.
    
    This patch removes the postponed 'next' member poisoning and adds
    documentation describing the ordering limitations in OVS RCU.
    
    Alex Wang dug out the root cause of the resulting crashes, thanks!
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
