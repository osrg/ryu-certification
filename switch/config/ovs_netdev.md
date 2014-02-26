---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
901ee2ee-4980-4ac2-a027-fbc369122ac4
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e85e8e2a-0ef5-4e08-a585-de8f7be41cf0
controller          : [5b32bc8a-0842-470e-b0d1-750fe44ce2a7]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [52439bd5-13a0-4671-902e-cb6f9cb56c5c, 6fce7697-c184-405b-b13b-1821810bed3e, e89126a3-d2b5-4f52-b868-02e5090d04e3]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5b32bc8a-0842-470e-b0d1-750fe44ce2a7
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=377, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 52439bd5-13a0-4671-902e-cb6f9cb56c5c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [16bfb23f-3efb-4f07-b48a-9eec0eb12ea2]
name                : br0

_uuid               : e89126a3-d2b5-4f52-b868-02e5090d04e3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [099a3884-cd12-4e64-8cd7-b6abe81f50b2]
name                : eth7

_uuid               : 6fce7697-c184-405b-b13b-1821810bed3e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [65d3d028-cc72-4813-876f-44b8a5bd9de9]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 65d3d028-cc72-4813-876f-44b8a5bd9de9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2810058, tx_dropped=0, tx_errors=0, tx_packets=29994}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 099a3884-cd12-4e64-8cd7-b6abe81f50b2
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
statistics          : {collisions=0, rx_bytes=3060189965, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72604055, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 16bfb23f-3efb-4f07-b48a-9eec0eb12ea2
admin_state         : up
duplex              : full
ifindex             : 356
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
commit 92ae5930c220d5994b691346526bde548ea97765
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Mon Feb 24 11:46:59 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Feb 26 08:18:03 2014 -0800

    socket-util: Fix set_dscp for IPv6
    
    Try IPPROTO_IPV6/IPV6_TCLASS socket option as well as IPPROTO_IP/IP_TOS
    so that this can work for IPv6 sockets.
    
    IPPROTO_IP/IP_TOS socket option is, as it's SOL indicates, for IPv4.
    What happens when it's used for IPv6 sockets?  On Linux, it seems to
    be forwarded to IPv4 code and affects IPv4 part of the socket.
    (e.g. non-V6ONLY case)  But it doesn't seem to be the intention of
    this function.  On other platforms including NetBSD, it just fails
    with ENOPROTOOPT.
    
    Probably this function should take the address family but passing
    it around lib/*stream*.c would be a bigger change.
    
    Cc: Arun Sharma &lt;arun.sharma@calsoftinc.com&gt;
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
