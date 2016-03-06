---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8cd2c2b6-3382-49c7-8d0a-e27b6e62aa81
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 952fdc0c-79ee-448a-98fa-83e454e9e040
controller          : [8174321f-e63a-416b-8fde-d79e18403db1]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [6aa73c8e-7616-41c9-b1fa-b8f9e85ae92a, 884d9e78-d69f-4cf3-b8b7-9be691e06a75, 8df6539a-d8d0-4a76-9f65-1cfa68be33f8, c05c12df-160d-4d97-81e7-0e09e6e1266a]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8174321f-e63a-416b-8fde-d79e18403db1
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="12", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 884d9e78-d69f-4cf3-b8b7-9be691e06a75
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [23f186a8-2410-49fa-a713-125165d6a238]
name                : "eth21"

_uuid               : 8df6539a-d8d0-4a76-9f65-1cfa68be33f8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [386cbcb0-085f-42fb-8971-0329ff00f8da]
name                : "eth22"

_uuid               : 6aa73c8e-7616-41c9-b1fa-b8f9e85ae92a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [77863e75-e65d-440b-928b-acb1ab508665]
name                : "br0"

_uuid               : c05c12df-160d-4d97-81e7-0e09e6e1266a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c453e863-5cb8-464e-8ebf-54828249618d]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 386cbcb0-085f-42fb-8971-0329ff00f8da
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31700128698, tx_dropped=0, tx_errors=0, tx_packets=21170393}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 23f186a8-2410-49fa-a713-125165d6a238
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
statistics          : {collisions=0, rx_bytes=47778729080, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31932466, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 77863e75-e65d-440b-928b-acb1ab508665
admin_state         : down
duplex              : full
ifindex             : 862
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

_uuid               : c453e863-5cb8-464e-8ebf-54828249618d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10503243000, tx_dropped=0, tx_errors=0, tx_packets=7002162}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6019cb63956dc87afd130c31ac17137d1304a931
Author:     Ilya Maximets &lt;i.maximets@samsung.com&gt;
AuthorDate: Thu Mar 3 11:30:06 2016 +0300
Commit:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
CommitDate: Sat Mar 5 20:15:25 2016 -0800

    netdev-dpdk: Fix memory leak in netdev_dpdk_vhost_destruct&#40;&#41;.
    
    Fixes: 4573fbd38fa1 &#40;&quot;netdev-dpdk: Add vhost-user multiqueue support&quot;&#41;
    Signed-off-by: Ilya Maximets &lt;i.maximets@samsung.com&gt;
    Acked-by: Flavio Leitner &lt;fbl@sysclose.org&gt;
    Acked-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>
