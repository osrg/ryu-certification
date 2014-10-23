---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
42a1b660-5181-47b7-a899-5add8e0b8b1b
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 49ec3f41-667f-4fc9-8be7-d04e0cfabf8f
controller          : [81b60bed-a28a-4316-87ec-7dfab15a4281]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [97384288-595b-495b-a5fa-25cc85e09773, 9b319aa0-3a23-4a1f-bf20-2cbb2957c6bb, d1724016-48bc-46a0-a6b1-8d7c00c2b980, ee40e489-863d-41b8-bd5d-bd78acc2d56a]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 81b60bed-a28a-4316-87ec-7dfab15a4281
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=687, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 97384288-595b-495b-a5fa-25cc85e09773
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6d944a2c-c36d-410d-9034-ec70972e5482]
name                : br0

_uuid               : 9b319aa0-3a23-4a1f-bf20-2cbb2957c6bb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1f2c330e-f511-4577-9dbe-1235efd434ed]
name                : eth21

_uuid               : ee40e489-863d-41b8-bd5d-bd78acc2d56a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [10539a22-e040-4f3a-8482-2f1d58d6ef8f]
name                : eth22

_uuid               : d1724016-48bc-46a0-a6b1-8d7c00c2b980
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [95ef6da0-92bc-4700-80bc-52a82f597b38]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 95ef6da0-92bc-4700-80bc-52a82f597b38
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3738530908, tx_dropped=0, tx_errors=0, tx_packets=8218977}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6d944a2c-c36d-410d-9034-ec70972e5482
admin_state         : down
duplex              : full
ifindex             : 279
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

_uuid               : 10539a22-e040-4f3a-8482-2f1d58d6ef8f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2571775192, tx_dropped=0, tx_errors=0, tx_packets=104836672}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 1f2c330e-f511-4577-9dbe-1235efd434ed
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
statistics          : {collisions=0, rx_bytes=2484837285, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=170687219, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 09cac43f740b0aef1ef1cb656d952f56bedd7fec
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Thu Oct 23 08:27:34 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Oct 23 13:29:23 2014 -0700

    dpif-netlink: Add support for packet receive on Windows.
    
    In this patch, we add support in dpif-netlink.c to receive packets on
    Windows. Windows does not natively support epoll&#40;&#41;. Even though there
    are mechanisms/interfaces that provide functionality similar to epoll&#40;&#41;,
    we take a simple approach of using a pool of sockets.
    
    Here are some details of the implementaion to aid review:
    1. There's pool of sockets per upcall handler.
    2. The pool of sockets is initialized while setting up the handler in
    dpif_netlink_refresh_channels&#40;&#41; primarily.
    3. When sockets are to be allocated for a vport, we walk through the
    pool of sockets for all handlers and pick one of the sockets in each of
    the pool. Within a handler's pool, sockets are picked in a round-robin
    fashion.
    4. We currently support only 1 handler, since there are some kernel
    changes needed for support more than 1 handler per vport.
    5. The pool size is also set to 1 currently.
    
    The restructions imposed by #4 and #5 can be removed in the future
    without much code churn.
    
    Validation:
    1. With a hacked up kernel which figures out the netlink socket that is
    designated to receive packets, we are cable to perform pings between 2
    VMs on the same Hyper-V host.
    2. Compiled the code in Linux as well.
    3. Tested with pool size == 2 as well, though in this patch we set the
    pool size = 1.
    
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
