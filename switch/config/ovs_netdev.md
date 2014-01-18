---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f0ef91a6-1a16-4a60-b077-c56d53272bd9
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 73cdedab-7ebd-47b9-ae78-b62758c397cf
controller          : [1c54a3b8-f543-496e-8748-1bed3d2adbef]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [6daddd78-d6a7-40ec-8878-6e4ffcde7b8a, 8ea2036a-9645-41b0-8602-edd1edda0c76, d8073b79-284c-4352-83ba-a69fb85aca16]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 1c54a3b8-f543-496e-8748-1bed3d2adbef
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=301, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6daddd78-d6a7-40ec-8878-6e4ffcde7b8a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0b6387ea-b73f-479d-bb0d-e7f312139a28]
name                : br0

_uuid               : d8073b79-284c-4352-83ba-a69fb85aca16
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4e02d6bc-916f-468b-9137-2d9c4f4726cd]
name                : eth8

_uuid               : 8ea2036a-9645-41b0-8602-edd1edda0c76
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [637ff828-468b-4653-ac72-e1f1bfc05e39]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4e02d6bc-916f-468b-9137-2d9c4f4726cd
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=910148, tx_dropped=0, tx_errors=0, tx_packets=9788}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 637ff828-468b-4653-ac72-e1f1bfc05e39
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=2871660, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29040, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 0b6387ea-b73f-479d-bb0d-e7f312139a28
admin_state         : up
duplex              : full
ifindex             : 115
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
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
commit 4ca828d713451307fea449be5111272f47c0c5a7
Author:     Linda Sun &lt;lsun@vmware.com&gt;
AuthorDate: Thu Jan 9 16:26:12 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Jan 17 16:11:20 2014 -0800

    poll-loop: Port to Windows.
    
    Use WaitForMultipleObjects for polling on windows.  This works on all kinds
    of objects, e.g. sockets, files, especially ioctl calls to the kernel.
    poll_fd_wait_event() is used if events need to be passed to pollfds.  latch
    is signaled with event, to be waited/polled by WaitForMultipleObjects() as
    well.  Changed array of fds to hmap to check for duplicate fds.
    
    Signed-off-by: Linda Sun &lt;lsun@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
