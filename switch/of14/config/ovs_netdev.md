---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a587a02a-babc-40fb-bdfc-fae5072808d6
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
_uuid               : ffbaf4bc-04b7-452c-93d9-e428d4547e3b
controller          : [a4010b94-207e-4b84-8df5-280aa5c5b535]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [27517622-9334-4083-a5f2-fc0635684e45, 367d78c0-e85d-4e5f-87e8-04b58309bd87, 544ef4e8-1c11-4766-9dc1-a4a27ac33f79, f5a94ab4-573a-494d-974b-fed3159b250b]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a4010b94-207e-4b84-8df5-280aa5c5b535
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f5a94ab4-573a-494d-974b-fed3159b250b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d4df4add-6352-4a67-94a8-a54f4641d24c]
name                : "eth23"

_uuid               : 367d78c0-e85d-4e5f-87e8-04b58309bd87
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [25a3c7db-2433-40b3-be36-79e7cae20f15]
name                : "eth21"

_uuid               : 544ef4e8-1c11-4766-9dc1-a4a27ac33f79
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [075a7f64-b5d5-4c1b-9bac-5b85ccc14762]
name                : "eth22"

_uuid               : 27517622-9334-4083-a5f2-fc0635684e45
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4b2dff59-5435-4ad5-ab52-22ecd4b9c63a]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 075a7f64-b5d5-4c1b-9bac-5b85ccc14762
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

_uuid               : 4b2dff59-5435-4ad5-ab52-22ecd4b9c63a
admin_state         : down
duplex              : full
ifindex             : 295
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

_uuid               : d4df4add-6352-4a67-94a8-a54f4641d24c
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

_uuid               : 25a3c7db-2433-40b3-be36-79e7cae20f15
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
commit 693e11384088643e2dcf7822e392d9a7af1f94b8
Author:     Gary Mussar &lt;gmussar@ciena.com&gt;
AuthorDate: Thu Jul 23 10:48:53 2015 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Tue Jul 28 14:00:54 2015 -0700

    dpdk: Fix detection of vhost_cuse in dpdk rte_config.h
    
    Dpdk allows users to create a config that includes other config files and
    then override values.
    
    Eg.
    defconfig_x86_64-native_vhost_cuse-linuxapp-gcc:
    
    CONFIG_RTE_BUILD_COMBINE_LIBS=y
    CONFIG_RTE_BUILD_SHARED_LIB=n
    CONFIG_RTE_LIBRTE_VHOST=y
    CONFIG_RTE_LIBRTE_VHOST_USER=n
    
    This allows you to have both a vhostuser and vhostcuse config in the same
    source tree without the need to replicate everything in those config files
    just to change a couple of settings. The resultant .config file has all of
    the settings from the included files with the updated settings at the end.
    The resultant rte_config.h contains multiple undefs and defines for the
    overridden settings.
    
    Eg.
      &gt; grep RTE_LIBRTE_VHOST_USER x86_64-native_vhost_cuse-linuxapp-gcc/include/rte_config.h
      #undef RTE_LIBRTE_VHOST_USER
      #define RTE_LIBRTE_VHOST_USER 1
      #undef RTE_LIBRTE_VHOST_USER
    
    The current mechanism to detect the RTE_LIBRTE_VHOST_USER setting merely
    greps the rte_config.h file for the string &quot;define RTE_LIBRTE_VHOST_USER 1&quot;
    rather than the final setting of RTE_LIBRTE_VHOST_USER. The following patch
    changes this test to detect the final setting of RTE_LIBRTE_VHOST_USER.
    
    Signed-off-by: Gary Mussar &lt;gmussar@ciena.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com
</pre>
