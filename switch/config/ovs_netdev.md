---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
5645db6d-8f4e-4f1d-a3b4-b7fbb9738681
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0dee2a96-242a-4fa1-84a8-a5ceedd4b602
controller          : [f591f239-9aee-4ad7-b7d4-3a0e03444a1b]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0ffe47e5-4948-4255-a624-0f95b477e99a, 9c85131c-0963-418f-bb86-dc2018ca6752, a49d36fd-a913-4998-b1c1-1ed70a750db7, bc63bf1d-4c22-4564-bc0b-cf53bedb226c]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f591f239-9aee-4ad7-b7d4-3a0e03444a1b
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=666, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9c85131c-0963-418f-bb86-dc2018ca6752
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3878a26c-9f2e-41cd-b5c5-ee5336e863cf]
name                : br0

_uuid               : 0ffe47e5-4948-4255-a624-0f95b477e99a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fd7434a2-59d0-4e0e-ab51-96cf48696358]
name                : eth22

_uuid               : bc63bf1d-4c22-4564-bc0b-cf53bedb226c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a025c669-4e9a-4f8a-bf70-4faf773d87f4]
name                : eth23

_uuid               : a49d36fd-a913-4998-b1c1-1ed70a750db7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [67fe58f2-3695-40fb-a2d3-e0284d41c2f7]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3878a26c-9f2e-41cd-b5c5-ee5336e863cf
admin_state         : down
duplex              : full
ifindex             : 96
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

_uuid               : a025c669-4e9a-4f8a-bf70-4faf773d87f4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3519496500, tx_dropped=0, tx_errors=0, tx_packets=2346331}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : fd7434a2-59d0-4e0e-ab51-96cf48696358
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1373872240, tx_dropped=0, tx_errors=0, tx_packets=23833863}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 67fe58f2-3695-40fb-a2d3-e0284d41c2f7
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
statistics          : {collisions=0, rx_bytes=3093548778, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=33584118, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
