---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f0e6fc46-e794-4777-8745-314a172ee9c1
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
_uuid               : e3af19de-561d-4fa1-bee6-736f470aff39
controller          : [fbe82bac-6c09-4674-a9a9-09d9634cee82]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2a87c303-d23e-4076-b6ef-d62097b3053a, 8aeb2377-ac64-4e26-872b-cd2afa981485, b4aaa2bc-c75f-4a17-945a-942ddb514d66]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : fbe82bac-6c09-4674-a9a9-09d9634cee82
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=302, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b4aaa2bc-c75f-4a17-945a-942ddb514d66
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c4d2e817-ecc6-4bc1-8d63-7b2d4bcb34a0]
name                : eth7

_uuid               : 2a87c303-d23e-4076-b6ef-d62097b3053a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7a3fb284-6653-413a-80fa-5895c8e5bed0]
name                : br0

_uuid               : 8aeb2377-ac64-4e26-872b-cd2afa981485
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [77d94f51-8bcb-4800-b2fb-6434c8186227]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7a3fb284-6653-413a-80fa-5895c8e5bed0
admin_state         : up
duplex              : full
ifindex             : 240
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

_uuid               : 77d94f51-8bcb-4800-b2fb-6434c8186227
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1849984, tx_dropped=0, tx_errors=0, tx_packets=19760}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : c4d2e817-ecc6-4bc1-8d63-7b2d4bcb34a0
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
statistics          : {collisions=0, rx_bytes=3057079177, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72572581, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c3fd6901f5d4436b92c675cdee6198786cd5a0ec
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Feb 11 15:13:56 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Feb 11 15:13:56 2014 -0800

    tunnel: Support all combinations of flow-based and specific tunnel matches.
    
    There are 12 possible ways to specify a tunnel (2 * 2 * 3 == 12):
    
        - Specific in_key or flow-based (2 choices).
    
        - Specific ip_dst or flow-based (2 choices).
    
        - Specific ip_src, wildcarded, or flow-based (3 choices).
    
    Until now, only 6 of the 12 possibilities have been supported.  We
    have had a couple of requests to add another.  This commit adds all the
    possibilities, so that we won't have to add the other 6 one by one.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Requested-by: Thomas Morin &lt;thomas.morin@orange.com&gt;
    Acked-by: pritesh &lt;pritesh.kothari@cisco.com&gt;
</pre>
