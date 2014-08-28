---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
5c6a7b9b-b9a0-4083-bea9-479cbe4da6bc
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : aa0f5b25-3f5c-4a5a-b93f-8c8e15c26d20
controller          : [68877e9c-18b4-4dbb-84a8-d7bafe3b6b02]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1464d619-145a-44b1-b0e3-528d095e9941, 46ba9d08-8b8e-4bc0-a7b2-5eba165c707f, 4e36b3e6-9f66-4f66-b252-4dd636e3ad7e, 7dff1ea0-f752-4978-a9f0-d16bee5213d0]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 68877e9c-18b4-4dbb-84a8-d7bafe3b6b02
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=677, sec_since_disconnect=7, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7dff1ea0-f752-4978-a9f0-d16bee5213d0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c724ae6d-0116-4ced-869a-f4cd2189f2dd]
name                : eth21

_uuid               : 46ba9d08-8b8e-4bc0-a7b2-5eba165c707f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9ef89c31-41c5-4d9a-80c3-978b3cd35d31]
name                : eth22

_uuid               : 1464d619-145a-44b1-b0e3-528d095e9941
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [657bd423-069d-49b3-8c2f-e5fa4a8a4732]
name                : br0

_uuid               : 4e36b3e6-9f66-4f66-b252-4dd636e3ad7e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cfe122c4-f5fd-44e8-a72d-b2754f1ad002]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : cfe122c4-f5fd-44e8-a72d-b2754f1ad002
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2337055500, tx_dropped=0, tx_errors=0, tx_packets=1558037}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c724ae6d-0116-4ced-869a-f4cd2189f2dd
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
statistics          : {collisions=0, rx_bytes=623333444, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=17611763, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9ef89c31-41c5-4d9a-80c3-978b3cd35d31
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2319539676, tx_dropped=0, tx_errors=0, tx_packets=13007032}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 657bd423-069d-49b3-8c2f-e5fa4a8a4732
admin_state         : down
duplex              : full
ifindex             : 71
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fd972eb87a888242fb1a8ec2394fa7b3030fbd7d
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Wed Aug 27 08:36:19 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Aug 28 08:52:52 2014 -0700

    netlink-socket: Use read/write ioctl instead of ReadFile/WriteFile.
    
    The Windows datapath supports a READ/WRITE ioctl instead of ReadFile/WriteFile.
    In this change, we update the following:
    - WriteFile&#40;&#41; in nl_sock_send__&#40;&#41; to use DeviceIoControl&#40;OVS_IOCTL_WRITE&#41;
    - ReadFile&#40;&#41; in nl_sock_recv__&#40;&#41; to use DeviceIoControl&#40;OVS_IOCTL_READ&#41;
    
    The WriteFile&#40;&#41; call in nl_sock_transact_multiple__&#40;&#41; has not been touched
    since it is not needed yet.
    
    Main motive for this change is to be able to unblock the DP Dump workflow.
    
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Eitan Eliahu &lt;eliahue@vmware.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
</pre>
