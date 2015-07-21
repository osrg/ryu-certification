---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
869c2bb1-39da-4910-9123-6c4479e07fbc
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 5b723380-0db3-41d9-9521-d655c4d031f2
controller          : [2678627a-9378-47ea-8cf8-9c6ecef5bef9]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [5e01acf8-2da1-4afc-a075-77318c681119, 889fc1f7-f87a-4bab-a86f-50442d21b0b4, af0bba6b-4d2d-4319-8ad5-03444a54817a, cb904d7c-5b40-4011-b2ad-a2cb0521786a]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2678627a-9378-47ea-8cf8-9c6ecef5bef9
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5e01acf8-2da1-4afc-a075-77318c681119
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d1ca2184-a712-4583-883b-e2538e8442ed]
name                : "eth21"

_uuid               : cb904d7c-5b40-4011-b2ad-a2cb0521786a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [62babf6a-3b0c-445a-9f83-d6f4c7b9a833]
name                : "br0"

_uuid               : af0bba6b-4d2d-4319-8ad5-03444a54817a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [581f21e3-0a1f-4164-8893-4abc7f575f32]
name                : "eth23"

_uuid               : 889fc1f7-f87a-4bab-a86f-50442d21b0b4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [71680faa-87a4-432e-a426-937578c519c5]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d1ca2184-a712-4583-883b-e2538e8442ed
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

_uuid               : 71680faa-87a4-432e-a426-937578c519c5
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

_uuid               : 62babf6a-3b0c-445a-9f83-d6f4c7b9a833
admin_state         : down
duplex              : full
ifindex             : 273
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

_uuid               : 581f21e3-0a1f-4164-8893-4abc7f575f32
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 4b8df0378747a83ec2478ded1e9cefe64d6a9f86
Author:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
AuthorDate: Thu Jul 16 19:48:23 2015 +0100
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Tue Jul 21 12:01:37 2015 -0700

    netdev-dpdk: Restore txq/rxq number if initialization fails.
    
    netdev_dpdk_set_multiq&#40;&#41; should not set the number of configured rxq
    and txq if the driver initialization fails &#40;meaning that the driver
    failed to setup the queues&#41;.  Otherwise, on a subsequent call to
    netdev_dpdk_set_multiq&#40;&#41;, the code may believe that the queues have
    already been setup and there's no work to be done.
    
    This commit fixes the problem by restoring the old values if
    dpdk_eth_dev_init&#40;&#41; fails.
    
    Reported-by: Ian Stokes &lt;ian.stokes@intel.com&gt;
    Tested-by: Ian Stokes &lt;ian.stokes@intel.com&gt;
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    Signed-off-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
