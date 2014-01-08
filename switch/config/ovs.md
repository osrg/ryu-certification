---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
dc6f6758-7911-4db6-9558-f1678a6a9810
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth8"
            Interface "eth8"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth7"
            Interface "eth7"

$ sudo ovs-vsctl list Bridge
_uuid               : df0d785b-d3c9-4a6a-b0f6-4864d9174d05
controller          : [f84d3907-dfe5-4668-bbf9-007df9f1ffad]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [120c9f3c-ce0e-4e0e-93b7-fd3c02c979b4, 857f8c71-801e-4871-82b5-39dc39030d07, c14e5aa7-1f5b-4821-afe5-4ad66d5b61fd]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : f84d3907-dfe5-4668-bbf9-007df9f1ffad
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="352", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 120c9f3c-ce0e-4e0e-93b7-fd3c02c979b4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9b0032c4-0ed8-42ee-8442-83aa643afcef]
name                : "eth8"

_uuid               : 857f8c71-801e-4871-82b5-39dc39030d07
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8fe4efd0-a737-48ca-ac16-97752967a46b]
name                : "br0"

_uuid               : c14e5aa7-1f5b-4821-afe5-4ad66d5b61fd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1990debd-cb1e-45f7-a7a2-3310e9edccb1]
name                : "eth7"

$ sudo ovs-vsctl list Interface
_uuid               : 9b0032c4-0ed8-42ee-8442-83aa643afcef
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:ec"
mtu                 : 1550
name                : "eth8"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 8fe4efd0-a737-48ca-ac16-97752967a46b
admin_state         : up
ifindex             : 113
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 1990debd-cb1e-45f7-a7a2-3310e9edccb1
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "eth7"
ofport              : 1
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5f67d45a0256558a9129d4cafd7fdca348d51290
Author:     Wei Yongjun &lt;yongjun_wei@trendmicro.com.cn&gt;
AuthorDate: Wed Jan 8 06:07:52 2014 -0800
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Wed Jan 8 06:07:52 2014 -0800

    datapath: Use kmem_cache_free() instead of kfree()
    
    memory allocated by kmem_cache_alloc() should be freed using
    kmem_cache_free(), not kfree().
    
    Fixes: e298e5057006 (openvswitch: Per cpu flow stats.)
    Signed-off-by: Wei Yongjun &lt;yongjun_wei@trendmicro.com.cn&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
