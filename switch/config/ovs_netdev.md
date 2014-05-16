---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b43bcd25-ee72-40ed-ab70-b107cfd1f508
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 91588794-bd96-4036-b3cc-9c090b216d12
controller          : [a2ceeb4d-36b1-46a0-a035-409f4fef9068]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [33d6bf47-cda4-4712-9143-a9f40935fb58, 3762d3d4-f08f-432f-9502-f9be91bccd7d, af4ab7ac-4a3a-47c5-be24-90f05829dfcb, f55568ab-a695-4afa-afaf-a1f19b53d785]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a2ceeb4d-36b1-46a0-a035-409f4fef9068
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=561, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3762d3d4-f08f-432f-9502-f9be91bccd7d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2a7c887d-1fe2-4e0b-a8e6-ab17e55e012b]
name                : eth23

_uuid               : af4ab7ac-4a3a-47c5-be24-90f05829dfcb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fdd1167e-822a-40c8-8e4b-9d2a68448a74]
name                : eth21

_uuid               : f55568ab-a695-4afa-afaf-a1f19b53d785
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e8afeafa-5a9c-462c-86e9-52481681ff20]
name                : eth22

_uuid               : 33d6bf47-cda4-4712-9143-a9f40935fb58
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5f2a34aa-0762-4a09-bc28-874af6b449dc]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2a7c887d-1fe2-4e0b-a8e6-ab17e55e012b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=146215500, tx_dropped=0, tx_errors=0, tx_packets=97477}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e8afeafa-5a9c-462c-86e9-52481681ff20
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=64171342, tx_dropped=0, tx_errors=0, tx_packets=43008}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 5f2a34aa-0762-4a09-bc28-874af6b449dc
admin_state         : down
duplex              : full
ifindex             : 33
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

_uuid               : fdd1167e-822a-40c8-8e4b-9d2a68448a74
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
statistics          : {collisions=0, rx_bytes=187032566, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=125315, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e09d61c41b4fe6559de4316d83d9221c254d4b0a
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Wed May 14 16:19:35 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri May 16 09:48:20 2014 -0700

    ovs-atomic: Remove atomic_uint64_t and atomic_int64_t.
    
    Some concern has been raised by Ben Pfaff that atomic_uint64_t may not
    be portable. In particular on 32bit platforms that do not have atomic
    64bit integers.
    
    Now that there are no longer any users of atomic_uint64_t remove it
    entirely. Also remove atomic_int64_t which has no users.
    
    Cc: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
