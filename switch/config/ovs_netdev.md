---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b1df42d0-ad05-4a13-968f-97a7f8c7343b
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 6da1e741-6711-4998-b5e5-371ec7e58d08
controller          : [4460b3cf-44f5-4f9d-8a1b-51e50726bfb4]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [06ee4034-dedd-40b9-9b81-6e5ac151ba4e, 0e928678-4265-42cb-abc9-0f3a27744ad2, 1e571900-e720-47fd-99be-bc22d0430346, e73eef9c-8f34-4411-86e1-5318a9d1bc67]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4460b3cf-44f5-4f9d-8a1b-51e50726bfb4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=967, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 06ee4034-dedd-40b9-9b81-6e5ac151ba4e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [47da3b0d-ebc6-4c5f-95b8-accd282bb953]
name                : eth23

_uuid               : 0e928678-4265-42cb-abc9-0f3a27744ad2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c30487cb-ad6d-40a7-b0c4-2808d35ef0f8]
name                : eth22

_uuid               : 1e571900-e720-47fd-99be-bc22d0430346
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [22b94873-12cd-454f-972b-ba1bbbd04c7d]
name                : br0

_uuid               : e73eef9c-8f34-4411-86e1-5318a9d1bc67
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [92a65447-8519-4e31-9c42-132fdaff326f]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 47da3b0d-ebc6-4c5f-95b8-accd282bb953
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4095218204, tx_dropped=0, tx_errors=0, tx_packets=5593457}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 92a65447-8519-4e31-9c42-132fdaff326f
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
statistics          : {collisions=0, rx_bytes=3749692701, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=11139671, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c30487cb-ad6d-40a7-b0c4-2808d35ef0f8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2844117622, tx_dropped=0, tx_errors=0, tx_packets=4777212}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 22b94873-12cd-454f-972b-ba1bbbd04c7d
admin_state         : down
duplex              : full
ifindex             : 366
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
commit c6bf49f3fad5833f8e228856e3bffe5885baf79c
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Wed May 28 17:00:48 2014 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Wed Jun 4 14:06:40 2014 -0700

    dpif: Fix slow action handling for DP_HASH and RECIRC
    
    In case DP_HASH and RECIRC actions need to be executed in slow path,
    current implementation simply don't handle them -- vswitchd simply
    crashes. This patch fixes them by supply an implementation for them.
    
    RECIRC will be handled by the datapath, same as the output action.
    
    DP_HASH, on the other hand, is handled in the user space. Although the
    resulting hash values may not match those computed by the datapath, it
    is less expensive; current use case &#40;bonding&#41; does not require a strict
    match to work properly.
    
    Reported-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
</pre>
