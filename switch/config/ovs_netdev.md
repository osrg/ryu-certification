---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0682b753-5162-4b6c-bf88-ed13a0ccdf2d
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 03496921-f718-4831-b021-b448aa701aad
controller          : [d75b8c66-007c-4373-a342-dae47e8fc411]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [409d2ea0-df06-42d6-98a5-cb7803215119, 4e5f34e8-6bdf-4dea-8ed7-bb5d55cdb68f, a376c0ff-fe1d-447d-9240-d139020c9496, f3b0aae2-f512-408b-a2d3-fb4f70f06080]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d75b8c66-007c-4373-a342-dae47e8fc411
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=561, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4e5f34e8-6bdf-4dea-8ed7-bb5d55cdb68f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d5aa1453-d87c-4d81-bc82-a1bf582954bc]
name                : eth22

_uuid               : 409d2ea0-df06-42d6-98a5-cb7803215119
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [da72cefa-af0e-42b4-a04a-63cd641ae7f0]
name                : eth21

_uuid               : f3b0aae2-f512-408b-a2d3-fb4f70f06080
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [491d0570-97e0-460f-b663-8d8c2185a960]
name                : eth23

_uuid               : a376c0ff-fe1d-447d-9240-d139020c9496
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [12a90b63-ba2f-4de0-bbe1-c997f913af72]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 491d0570-97e0-460f-b663-8d8c2185a960
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=292527000, tx_dropped=0, tx_errors=0, tx_packets=195018}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : da72cefa-af0e-42b4-a04a-63cd641ae7f0
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
statistics          : {collisions=0, rx_bytes=374065132, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=250630, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 12a90b63-ba2f-4de0-bbe1-c997f913af72
admin_state         : down
duplex              : full
ifindex             : 39
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

_uuid               : d5aa1453-d87c-4d81-bc82-a1bf582954bc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=128249684, tx_dropped=0, tx_errors=0, tx_packets=85954}
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
