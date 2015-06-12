---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ef22bec6-bbd3-4ded-9ffb-8b3841406eae
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
_uuid               : 75413602-c436-4e2c-8b06-f5eb15b85f34
controller          : [bcfd925b-3f8b-4f62-a3aa-5863bcf074c8]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [dbabff8e-0941-4f4b-ab8f-1e0f3b4b1507, df37fcf5-bb56-4b34-844d-a141922dcea3, ea02c099-659d-4ba7-9a31-481cd0da94a5, f8c14ed5-93ca-4e0c-8a2c-cf5792dac414]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : bcfd925b-3f8b-4f62-a3aa-5863bcf074c8
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ea02c099-659d-4ba7-9a31-481cd0da94a5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bf67abbc-4101-4889-a329-05ee9aa73300]
name                : "br0"

_uuid               : f8c14ed5-93ca-4e0c-8a2c-cf5792dac414
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [116da267-2624-4cb3-b977-d70b2ae5d361]
name                : "eth22"

_uuid               : df37fcf5-bb56-4b34-844d-a141922dcea3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [66ae9cd7-d56a-4664-8bd2-1d71a3128b36]
name                : "eth21"

_uuid               : dbabff8e-0941-4f4b-ab8f-1e0f3b4b1507
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a0687d65-3460-4f51-9569-ada5e565c938]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : bf67abbc-4101-4889-a329-05ee9aa73300
admin_state         : down
duplex              : full
ifindex             : 149
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

_uuid               : a0687d65-3460-4f51-9569-ada5e565c938
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

_uuid               : 116da267-2624-4cb3-b977-d70b2ae5d361
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

_uuid               : 66ae9cd7-d56a-4664-8bd2-1d71a3128b36
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
