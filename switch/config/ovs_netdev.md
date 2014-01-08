---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b1b9d98b-eeee-4624-a9dd-e181c11689ac
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth8"
            Interface "eth8"
        Port "eth7"
            Interface "eth7"

$ sudo ovs-vsctl list Bridge
_uuid               : 4c1ebe61-50f9-4e55-ab11-b48aec29115d
controller          : [3b6d2726-6664-49dc-9057-200d8b7ccd5f]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [00025036-2afa-4026-9cf0-3575ea1b7cd7, 4bcfb513-98d6-4e29-80b9-906119898324, e80309b7-ce9f-4a98-8862-c11fb10ae597]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 3b6d2726-6664-49dc-9057-200d8b7ccd5f
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="291", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 00025036-2afa-4026-9cf0-3575ea1b7cd7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [54572e28-e131-4609-99a5-e8aa1dd98fcd]
name                : "br0"

_uuid               : 4bcfb513-98d6-4e29-80b9-906119898324
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e1bb76a7-2c6e-46c2-b711-5a4a338f41a8]
name                : "eth8"

_uuid               : e80309b7-ce9f-4a98-8862-c11fb10ae597
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7c1c4cee-862a-4bbc-82a7-00a9fa222208]
name                : "eth7"

$ sudo ovs-vsctl list Interface
_uuid               : 54572e28-e131-4609-99a5-e8aa1dd98fcd
admin_state         : up
duplex              : full
ifindex             : 111
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : 7c1c4cee-862a-4bbc-82a7-00a9fa222208
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
statistics          : {collisions=0, rx_bytes=2399126, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=24382, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : e1bb76a7-2c6e-46c2-b711-5a4a338f41a8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=809700, tx_dropped=0, tx_errors=0, tx_packets=8734}
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
