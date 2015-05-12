---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
039f0b2d-ec6e-4275-b1ef-cc9b94684bc9
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f155c7a4-91ca-47c5-ae44-5b7b2ef673c1
controller          : [edf2f74b-fd1c-4b77-af64-faac23e5ddb0]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [70e632b0-a616-479d-81bd-e6b2a49772cf, 9d113013-f7fa-41f0-91d7-71e39f8d0fa6, 9d2263bd-eb5c-491d-8f62-4daa519db713, fd2b39d3-7b9b-4b5d-af6c-113cd569df02]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : edf2f74b-fd1c-4b77-af64-faac23e5ddb0
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 70e632b0-a616-479d-81bd-e6b2a49772cf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [478ec60b-c65b-45cd-b354-d15c3d2d93a7]
name                : "br0"

_uuid               : 9d2263bd-eb5c-491d-8f62-4daa519db713
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1f142680-070c-4d15-9272-6b8f896f0e15]
name                : "eth21"

_uuid               : fd2b39d3-7b9b-4b5d-af6c-113cd569df02
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [20b4f0ea-65d6-4e7f-8e7e-24632bda693e]
name                : "eth23"

_uuid               : 9d113013-f7fa-41f0-91d7-71e39f8d0fa6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d5f93766-48e6-4cb4-bf14-2913f0e26e03]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1f142680-070c-4d15-9272-6b8f896f0e15
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
statistics          : {collisions=0, rx_bytes=12162578921, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=8114286, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 20b4f0ea-65d6-4e7f-8e7e-24632bda693e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=660771000, tx_dropped=0, tx_errors=0, tx_packets=440514}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d5f93766-48e6-4cb4-bf14-2913f0e26e03
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9832850755, tx_dropped=0, tx_errors=0, tx_packets=6557815}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 478ec60b-c65b-45cd-b354-d15c3d2d93a7
admin_state         : down
duplex              : full
ifindex             : 41
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9899125aaae9f0634f43307cc0ff72f5afb287bb
Author:     Oleg Strikov &lt;oleg.strikov@canonical.com&gt;
AuthorDate: Fri May 8 12:05:13 2015 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Tue May 12 09:14:12 2015 -0700

    INSTALL.DPDK: Notes on running ovs-vswitchd/dpdk inside a VM
    
    Additional configuration is required if you want to run ovs-vswitchd
    with DPDK backend inside a QEMU virtual machine. This happens because,
    by default, virtio NIC provided to the guest doesn't support multiple
    TX queues which are required by ovs-vswitchd/dpdk. This commit updates
    INSTALL.DPDK.md to provide guidelines on how to enable support for
    multiple TX queues using QEMU command line and Libvirt config file.
    
    Signed-off-by: Oleg Strikov &lt;oleg.strikov@canonical.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
