---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c0cebd83-8f74-4b80-81a1-1452d67fe15d
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : eb12e139-b227-413b-9679-2b0fbe3a4bdb
controller          : [5bf4e526-7f7c-4e54-9787-3e65a80c5277]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [06413dca-28c6-42be-9a74-3ecbbef1e9ab, 842b2ee8-3dd6-46a8-a998-a9dfe3dacae0, 95ca89f9-f40e-4852-b20c-140d01eb4193, a4aac049-d0bc-4036-9da6-a526e1e9d337]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5bf4e526-7f7c-4e54-9787-3e65a80c5277
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 842b2ee8-3dd6-46a8-a998-a9dfe3dacae0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [78393960-052b-45f5-9933-fa37d144ec79]
name                : "br0"

_uuid               : 95ca89f9-f40e-4852-b20c-140d01eb4193
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1a5f180f-6407-4d25-984d-379e32d388f1]
name                : "eth21"

_uuid               : a4aac049-d0bc-4036-9da6-a526e1e9d337
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9541aba2-c05c-4e1a-be88-774c8579fc8e]
name                : "eth23"

_uuid               : 06413dca-28c6-42be-9a74-3ecbbef1e9ab
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fd16b5e4-75f8-4623-8d3a-5ebf19a5b7eb]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : fd16b5e4-75f8-4623-8d3a-5ebf19a5b7eb
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

_uuid               : 78393960-052b-45f5-9933-fa37d144ec79
admin_state         : down
duplex              : full
ifindex             : 321
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

_uuid               : 9541aba2-c05c-4e1a-be88-774c8579fc8e
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

_uuid               : 1a5f180f-6407-4d25-984d-379e32d388f1
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
commit 2aca813cf4dfd870232d708cda34017e3888333f
Author:     Ilya Maximets &lt;i.maximets@samsung.com&gt;
AuthorDate: Tue Aug 4 12:36:37 2015 -0700
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Tue Aug 4 12:36:45 2015 -0700

    dpif-netdev: fix race for queues between pmd threads.
    
    Currently pmd threads select queues in pmd_load_queues&#40;&#41; according to
    get_n_pmd_threads_on_numa&#40;&#41;. This behavior leads to race between pmds,
    beacause dp_netdev_set_pmds_on_numa&#40;&#41; starts them one by one and
    current number of threads changes incrementally.
    
    As a result we may have the following situation with 2 pmd threads:
    
    * dp_netdev_set_pmds_on_numa&#40;&#41;
    * pmd12 thread started. Currently only 1 pmd thread exists.
    dpif_netdev&#40;pmd12&#41;|INFO|Core 1 processing port 'port_1'
    dpif_netdev&#40;pmd12&#41;|INFO|Core 1 processing port 'port_2'
    * pmd14 thread started. 2 pmd threads exists.
    dpif_netdev|INFO|Created 2 pmd threads on numa node 0
    dpif_netdev&#40;pmd14&#41;|INFO|Core 2 processing port 'port_2'
    
    We have:
    core 1 --&gt; port 1, port 2
    core 2 --&gt; port 2
    
    Fix this by starting pmd threads only after all of them have
    been configured.
    
    Cc: Daniele Di Proietto &lt;diproiettod at vmware.com&gt;
    Cc: Dyasly Sergey &lt;s.dyasly at samsung.com&gt;
    
    Acked-by: Flavio Leitner &lt;fbl@sysclose.org&gt;
    Acked-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    
    Signed-off-by: Ilya Maximets &lt;i.maximets at samsung.com&gt;
    Signed-off-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
