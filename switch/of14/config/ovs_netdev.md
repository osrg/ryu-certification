---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
29395781-dd33-4c09-90be-baaba4caec88
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : dd6112ff-72da-4a0f-944c-1f3308bc5561
controller          : [25e56acd-3baa-4eb6-845a-bc108cc38f23]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [3de01e5c-bc44-4477-b91b-05f1a92eea12, 6b3f065f-60a2-4313-9198-13ddf237a023, 6f518bd4-de46-40fc-8535-4ff8dd2c7c16, d8aa65ca-1670-4b65-999a-f0c1bf60b276]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 25e56acd-3baa-4eb6-845a-bc108cc38f23
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=671, sec_since_disconnect=6, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6f518bd4-de46-40fc-8535-4ff8dd2c7c16
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [00d0d9b8-ee93-4f14-a3b3-6997c99f7833]
name                : br0

_uuid               : 3de01e5c-bc44-4477-b91b-05f1a92eea12
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [46219a31-75e2-4772-b3e3-cb8b4a1c715f]
name                : eth21

_uuid               : d8aa65ca-1670-4b65-999a-f0c1bf60b276
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [73de03ff-6aff-4bb1-9bf5-eec520b49ca8]
name                : eth22

_uuid               : 6b3f065f-60a2-4313-9198-13ddf237a023
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [47ae3762-61cb-485b-a166-4e83a8858449]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 00d0d9b8-ee93-4f14-a3b3-6997c99f7833
admin_state         : down
duplex              : full
ifindex             : 138
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 46219a31-75e2-4772-b3e3-cb8b4a1c715f
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=3365626870, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=65277549, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 47ae3762-61cb-485b-a166-4e83a8858449
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1277592704, tx_dropped=0, tx_errors=0, tx_packets=3715040}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 73de03ff-6aff-4bb1-9bf5-eec520b49ca8
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3697979644, tx_dropped=0, tx_errors=0, tx_packets=45433553}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 65f13b50c5aaa9afaef397ee8252647f1ef1688d
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Fri Sep 5 14:14:20 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Mon Sep 15 11:43:49 2014 -0700

    dpif-netdev: Create multiple pmd threads by default.
    
    With this commit, ovs by default will create one pmd thread
    for each numa node and pin the pmd thread to available cpu
    core on the numa node.
    
    NON_PMD_CORE_ID &#40;currently 0&#41; is used to reserve a particular
    cpu core for the I/O of all non-pmd threads.  No pmd thread
    can be pinned to this reserved core.
    
    As side-effects of this commit:
    
    -  pmd thread will not be created, if there is no dpdk interface
       from the corresponding numa node added to ovs.
    
    - the exact-match cache for non-pmd threads is removed from
      'struct dp_netdev'.  Instead, all non-pmd threads will use
      the exact-match cache defined in the 'struct dp_netdev_pmd_thread'
      for NON_PMD_CORE_ID.
    
    - the rx packet processing functions are refactored to use
      'struct dp_netdev_pmd_thread' as input.
    
    - the 'netdev_send&#40;&#41;' function will be called with the proper
      queue id.
    
    - both pmd and non-pmd threads can call the dpif_netdev_execute&#40;&#41;.
      so, use a per-thread key to help recognize the calling thread.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
