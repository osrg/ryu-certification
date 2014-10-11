---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
24cad759-f9a8-48dd-aee4-cbf7b1c18a2f
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8658af05-c440-408d-9fe6-445a5596a7cf
controller          : [21af9722-6b30-4533-918e-1373ab1517af]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [8b532778-6c4e-4971-9810-234442178ba9, a70e9327-8b52-4f9e-a5ea-8f24593bf6b9, ac445cd7-e012-4edd-a05a-0892b6b2055a, d51c2fb5-32a2-4d95-8893-c40c5faf2584]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 21af9722-6b30-4533-918e-1373ab1517af
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=677, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8b532778-6c4e-4971-9810-234442178ba9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b0da38ce-afd6-4e1d-b304-fa1524963572]
name                : br0

_uuid               : d51c2fb5-32a2-4d95-8893-c40c5faf2584
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6caf0184-2b7b-405e-818e-aaa135a30508]
name                : eth23

_uuid               : ac445cd7-e012-4edd-a05a-0892b6b2055a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b45b0494-e55b-46dd-bed5-d0f96a4f954d]
name                : eth21

_uuid               : a70e9327-8b52-4f9e-a5ea-8f24593bf6b9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d3d3ee5f-ee61-4842-af78-476a553fefa2]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6caf0184-2b7b-405e-818e-aaa135a30508
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1869254908, tx_dropped=0, tx_errors=0, tx_packets=6972793}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b45b0494-e55b-46dd-bed5-d0f96a4f954d
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
statistics          : {collisions=0, rx_bytes=1660619241, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=161534154, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b0da38ce-afd6-4e1d-b304-fa1524963572
admin_state         : down
duplex              : full
ifindex             : 238
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

_uuid               : d3d3ee5f-ee61-4842-af78-476a553fefa2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2281725614, tx_dropped=0, tx_errors=0, tx_packets=98910363}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ff601a08a44c37fa8a6e0e569dc00d6731f55555
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Fri Oct 10 14:41:10 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Fri Oct 10 16:07:32 2014 -0700

    ofproto-dpif-upcall: Fix out-of-scope use of stack memory.
    
    Commit cc377352d &#40;ofproto: Reorganize in preparation for direct
    dpdk upcalls.&#41; introduced the bug that keeps reference to 'struct
    flow' defined on the stack inside while loop when running out of
    the scope.  This causes strange bug like wrong mask extraction
    when the part of memory is corrupted, and could lead to even
    more serious bug/crash.
    
    This commit fixes the above issue by defining an array of the
    'struct flow's on the function stack.
    
    Found by running ovs on RHEL7.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
