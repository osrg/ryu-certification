---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
bd5e787f-a8bd-419d-9be5-d4e8c1dcfa7c
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
_uuid               : d586f18b-e200-453d-996a-7d90c46e8b3e
controller          : [cfb5b231-254b-49ac-a662-e5fc5659c880]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [05d24f46-83e1-4e42-8abf-a76d3651ac76, 76114846-9ba6-4d39-afbc-51ac168deefc, 95a81615-e32e-45ed-a32f-5fce24a5d4a6, b7af999a-03ac-4462-a307-69ecc512260a]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : cfb5b231-254b-49ac-a662-e5fc5659c880
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 95a81615-e32e-45ed-a32f-5fce24a5d4a6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [eddbb0b7-c7d1-464a-82e4-f18dc61f5f1c]
name                : "eth22"

_uuid               : 76114846-9ba6-4d39-afbc-51ac168deefc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1d69517a-d892-4601-b4e0-dce61d96dc2c]
name                : "br0"

_uuid               : b7af999a-03ac-4462-a307-69ecc512260a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3d2b7530-37ab-4297-87bd-01bd0088781e]
name                : "eth21"

_uuid               : 05d24f46-83e1-4e42-8abf-a76d3651ac76
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7f0bb1d1-3e6c-437a-a32c-071c1aefd6c5]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3d2b7530-37ab-4297-87bd-01bd0088781e
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

_uuid               : 7f0bb1d1-3e6c-437a-a32c-071c1aefd6c5
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

_uuid               : 1d69517a-d892-4601-b4e0-dce61d96dc2c
admin_state         : down
duplex              : full
ifindex             : 417
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

_uuid               : eddbb0b7-c7d1-464a-82e4-f18dc61f5f1c
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
commit e4e74c3a2b9a83544cb976e5049fb65da9ecbed5
Author:     Alex Wang &lt;ee07b291@gmail.com&gt;
AuthorDate: Tue Aug 25 16:36:46 2015 -0700
Commit:     Alex Wang &lt;ee07b291@gmail.com&gt;
CommitDate: Wed Sep 2 05:57:59 2015 +0000

    dpif-netdev: Purge all ukeys when reconfigure pmd.
    
    When dpdk configuration changes, all pmd threads are recreated
    and rx queues of each port are reloaded.  After this process,
    rx queue could be mapped to a different pmd thread other than
    the one before reconfiguration.  However, this is totally
    transparent to ofproto layer modules.  So, if the ofproto-dpif-upcall
    module still holds ukeys generated before pmd thread recreation,
    this old ukey will collide with the ukey for the new upcalls
    from same traffic flow, causing flow installation failure.
    
    To fix the bug, this commit adds a new call-back function
    in dpif layer for notifying upper layer the purging of datapath
    &#40;e.g. pmd thread deletion in dpif-netdev&#41;.  So, the
    ofproto-dpif-upcall module can react properly with deleting
    the ukeys and with collecting flows' last stats.
    
    Reported-by: Ilya Maximets &lt;i.maximets@samsung.com&gt;
    Signed-off-by: Alex Wang &lt;ee07b291@gmail.com&gt;
    Acked-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    Tested-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
