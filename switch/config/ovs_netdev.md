---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8e5874c3-1286-463a-8477-f8b6f4bb3640
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f09036ad-d7fd-4ffa-ad38-b9c1a0703bd6
controller          : [8f46029b-4425-431e-ba71-59f5587d4dc1]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0a3f0082-a181-40ec-9732-3243dce43c6f, 15549ab8-9cc0-46a6-a351-cf03b657a66f, ac6d894e-ffea-495d-8815-663c4157d3a3, b7252a3c-b317-43fa-af4e-b46bcb3fa1ca]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8f46029b-4425-431e-ba71-59f5587d4dc1
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=562, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 15549ab8-9cc0-46a6-a351-cf03b657a66f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a44b4a7b-ad37-4efd-adda-72d1cea00fe6]
name                : eth23

_uuid               : b7252a3c-b317-43fa-af4e-b46bcb3fa1ca
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [35bd2e59-bbde-416b-b1dc-9f2b625ae81c]
name                : br0

_uuid               : 0a3f0082-a181-40ec-9732-3243dce43c6f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cd0c6fee-4254-4c08-9b56-bff4d307fcca]
name                : eth22

_uuid               : ac6d894e-ffea-495d-8815-663c4157d3a3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6acc7a72-3332-4f87-99df-ccef4dc7c213]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 35bd2e59-bbde-416b-b1dc-9f2b625ae81c
admin_state         : down
duplex              : full
ifindex             : 107
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

_uuid               : cd0c6fee-4254-4c08-9b56-bff4d307fcca
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1183665204, tx_dropped=0, tx_errors=0, tx_packets=792407}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6acc7a72-3332-4f87-99df-ccef4dc7c213
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
statistics          : {collisions=0, rx_bytes=2945144571, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1972137, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a44b4a7b-ad37-4efd-adda-72d1cea00fe6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2041693500, tx_dropped=0, tx_errors=0, tx_packets=1361129}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e262505ce4b908307441478a9b65e1bb22760e0c
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Wed May 21 08:31:47 2014 +0900
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Tue May 20 17:12:35 2014 -0700

    datapath: 16bit inner_network_header field in struct ovs_gso_cb
    
    The motivation for this is to create a 16bit hole in struct ovs_gso_cb
    which may be used for the inner_protocol field which is needed
    for the proposed implementation of compatibility for MPLS GSO segmentation.
    
    This should be safe as inner_network_header is now an offset to
    the inner_mac_header rather than skb-&gt;head.
    
    As pointed out by Thomas Graf simply making both inner offsets 16bis is not
    safe as there have been cases of overflow with &quot;with collapsed TCP frames
    on IB when the headroom grew beyond 64K. See commit 50bceae9bd tcp:
    Reallocate headroom if it would overflow csum_start'' for additional
    details.&quot;
    
    This patch is based on suggestions by Thomas Graf and Jesse Gross.
    
    Cc: Thomas Graf &lt;tgraf@suug.ch&gt;
    Cc: Jesse Gross &lt;jesse@nicira.com&gt;
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
