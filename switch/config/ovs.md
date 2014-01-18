---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0c275d83-feff-4e2e-9e33-b6228486c715
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b3a73025-52e8-4126-8a78-d185c081afcf
controller          : [58d47c77-7d74-43fe-96f5-19048b9ab036]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4353c3c7-3abb-4459-be46-9954a5f28e42, 5852729d-77be-4b2f-bf26-f945799f31e2, e3e0b299-2480-4822-ba90-087406a71dcb]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 58d47c77-7d74-43fe-96f5-19048b9ab036
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e3e0b299-2480-4822-ba90-087406a71dcb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8114d72f-5bab-479f-9920-9c8d8242cff5]
name                : br0

_uuid               : 5852729d-77be-4b2f-bf26-f945799f31e2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b67b2d24-23be-4297-bafd-54f0650a57cd]
name                : eth7

_uuid               : 4353c3c7-3abb-4459-be46-9954a5f28e42
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [038ddf47-d3a2-4be6-8964-19c9ef17eb65]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b67b2d24-23be-4297-bafd-54f0650a57cd
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
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 8114d72f-5bab-479f-9920-9c8d8242cff5
admin_state         : up
ifindex             : 117
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 038ddf47-d3a2-4be6-8964-19c9ef17eb65
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
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
