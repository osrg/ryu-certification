---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d9b64051-1d34-457c-9c5e-d02f5d5891f5
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 9bec0956-015d-4505-92b5-ca4046cc8e89
controller          : [84ca39db-0f1e-4752-9f3d-461c20e8cc13]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [592f4052-7c26-4f4d-a1d9-2367e9b44fa2, 85831534-ca27-4d33-8c9e-40672b127887, 87034110-4353-4a2e-b658-f2785961a883, fa896b25-0b15-4ae2-852c-1c213bcce9da]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 84ca39db-0f1e-4752-9f3d-461c20e8cc13
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=667, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 85831534-ca27-4d33-8c9e-40672b127887
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f3fc7276-0c72-4089-a94b-4177d16b83e4]
name                : br0

_uuid               : 87034110-4353-4a2e-b658-f2785961a883
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [77941789-a877-4b0c-a930-beab02c0c7ef]
name                : eth23

_uuid               : fa896b25-0b15-4ae2-852c-1c213bcce9da
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bc6e2cb4-f682-4aeb-a10b-59d73857e93c]
name                : eth22

_uuid               : 592f4052-7c26-4f4d-a1d9-2367e9b44fa2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2d3cf6b1-9131-440e-bd23-fdbe2d7d6841]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : bc6e2cb4-f682-4aeb-a10b-59d73857e93c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2278523516, tx_dropped=0, tx_errors=0, tx_packets=12979395}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 77941789-a877-4b0c-a930-beab02c0c7ef
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2237850000, tx_dropped=0, tx_errors=0, tx_packets=1491900}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2d3cf6b1-9131-440e-bd23-fdbe2d7d6841
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
statistics          : {collisions=0, rx_bytes=506471736, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=17533224, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f3fc7276-0c72-4089-a94b-4177d16b83e4
admin_state         : down
duplex              : full
ifindex             : 69
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
