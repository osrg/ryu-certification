---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b78000d7-fba5-469b-84ff-c373bb98558e
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : de9fa0c6-1157-4f40-a80b-db8113dd440a
controller          : [6b74d825-2287-4d26-9eba-45c546c720ad]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [25f299e1-190f-40f4-a680-1cce3a207545, 491a9255-d6fd-466c-a65d-f99bb3372248, d1ad7b2d-7c43-40ca-b719-58a433dcb440, ffddd3ff-8ee2-4367-95f5-0a69ab4347f6]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6b74d825-2287-4d26-9eba-45c546c720ad
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=661, sec_since_disconnect=6, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 25f299e1-190f-40f4-a680-1cce3a207545
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e5d96480-14c4-4937-94ef-c37a888929a5]
name                : eth22

_uuid               : d1ad7b2d-7c43-40ca-b719-58a433dcb440
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [304c97ab-5b9c-417a-98e1-d778ebcb1581]
name                : eth23

_uuid               : 491a9255-d6fd-466c-a65d-f99bb3372248
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c706d23e-d3f5-4e74-86dd-7cded080f45b]
name                : eth21

_uuid               : ffddd3ff-8ee2-4367-95f5-0a69ab4347f6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3ee660f1-a7a1-43e8-8873-44612c7dd0f6]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e5d96480-14c4-4937-94ef-c37a888929a5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1489127626, tx_dropped=0, tx_errors=0, tx_packets=23911186}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3ee660f1-a7a1-43e8-8873-44612c7dd0f6
admin_state         : down
duplex              : full
ifindex             : 99
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

_uuid               : c706d23e-d3f5-4e74-86dd-7cded080f45b
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
statistics          : {collisions=0, rx_bytes=3315660616, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=33733224, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 304c97ab-5b9c-417a-98e1-d778ebcb1581
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3670753500, tx_dropped=0, tx_errors=0, tx_packets=2447169}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit b0e1bce5d6528d71605f0d75e47f5f14d4b04f0d
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Thu Aug 28 09:25:56 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Thu Sep 4 18:38:26 2014 -0700

    cccl: Ability to enable compiler optimization.
    
    MSVC has a '-O2' compiler optimization flag which makes code run
    fast and is the recommended option for released code. For e.g.,
    running &quot;./tests/ovstest.exe test-cmap benchmark 1000000 3 1&quot;
    shows a 3x improvement for some cmap micro-benchmarks.
    
    In the Visual Studio world, there is a concept of &quot;release&quot; build
    &#40;fast code, harder to debug&#41; and a &quot;debug&quot; build &#40;easier to debug&#41;.
    The IDE provides this option and the IDE users expect something similar
    for command line build.
    
    So this commit, introduces a &quot;--with-debug&quot; configure option for Windows
    and does not use '-O2' as a compiler option when specified. This can
    be extended further if there are more compiler options that distinguish
    a &quot;release&quot; build vs &quot;debug&quot; build.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Saurabh Shah &lt;ssaurabh@vmware.com&gt;
</pre>
