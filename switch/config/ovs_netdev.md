---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0a6288b6-942a-4692-8eda-3f4a13d3b855
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
_uuid               : 7fb564c5-c5d0-4ef6-9f43-56fab819d4d6
controller          : [ff88356d-92ae-4db2-b31b-34f7b8504a92]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [247a33fb-4a33-4ed5-8b90-75dd229291ab, 68857139-c578-47a5-b37d-afb006b92116, b5feaff4-affe-4c43-9b93-aa6bdbc649a7]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ff88356d-92ae-4db2-b31b-34f7b8504a92
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=316, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b5feaff4-affe-4c43-9b93-aa6bdbc649a7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8666417c-1a9b-49f1-bcbc-0e03f40e4906]
name                : br0

_uuid               : 68857139-c578-47a5-b37d-afb006b92116
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [95d37713-1ee8-4b47-a61e-31eeb4bed46f]
name                : eth7

_uuid               : 247a33fb-4a33-4ed5-8b90-75dd229291ab
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7c02d0c1-f7de-4231-99bc-a1b192cb52c6]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8666417c-1a9b-49f1-bcbc-0e03f40e4906
admin_state         : up
duplex              : full
ifindex             : 809
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

_uuid               : 7c02d0c1-f7de-4231-99bc-a1b192cb52c6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6203566, tx_dropped=0, tx_errors=0, tx_packets=66129}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 95d37713-1ee8-4b47-a61e-31eeb4bed46f
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
statistics          : {collisions=0, rx_bytes=3071713502, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72720996, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 437d0d22ab42d4101157b48a75fa844e7039e326
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Mon Mar 24 09:17:01 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Sat Mar 29 17:22:19 2014 -0700

    lib/ofpbuf: Compact
    
    This patch shrinks the struct ofpbuf from 104 to 48 bytes on 64-bit
    systems, or from 52 to 36 bytes on 32-bit systems (counting in the
    'l7' removal from an earlier patch).  This may help contribute to
    cache efficiency, and will speed up initializing, copying and
    manipulating ofpbufs.  This is potentially important for the DPDK
    datapath, but the rest of the code base may also see a little benefit.
    
    Changes are:
    
    - Remove 'l7' pointer (previous patch).
    - Use offsets instead of layer pointers for l2_5, l3, and l4 using
      'l2' as basis.  Usually 'data' is the same as 'l2', but this is not
      always the case (e.g., when parsing or constructing a packet), so it
      can not be easily used as the offset basis.  Also, packet parsing is
      faster if we do not need to maintain the offsets each time we pull
      data from the ofpbuf.
    - Use uint32_t for 'allocated' and 'size', as 2^32 is enough even for
      largest possible messages/packets.
    - Use packed enum for 'source'.
    - Rearrange to avoid unnecessary padding.
    - Remove 'private_p', which was used only in two cases, both of which
      had the invariant ('l2' == 'data'), so we can temporarily use 'l2'
      as a private pointer.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
