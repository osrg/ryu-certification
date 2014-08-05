---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f1f61519-c6af-4f85-8568-1191bc05fc82
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f7129b54-58ac-4935-9a5b-3cd5ab6ecd38
controller          : [5f9821aa-712c-455e-86a0-91bd7ba3ae57]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1077897a-c584-4746-8b0f-91dbf514e439, 73a0a63a-1d97-41ec-8c6b-f57ba785187f, 9982793a-f200-4d0b-bd5f-5807ddd72ab2, a895f204-2771-4cf9-9d01-8f1b0e833b1f]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5f9821aa-712c-455e-86a0-91bd7ba3ae57
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=687, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a895f204-2771-4cf9-9d01-8f1b0e833b1f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a20a782f-fc63-413e-b2df-66e8a5bb9de2]
name                : eth22

_uuid               : 73a0a63a-1d97-41ec-8c6b-f57ba785187f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8458216c-76a1-4cd4-b3da-3682d6ddbdb8]
name                : br0

_uuid               : 1077897a-c584-4746-8b0f-91dbf514e439
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1ffe157c-9b78-46d5-a87f-b121fd385680]
name                : eth23

_uuid               : 9982793a-f200-4d0b-bd5f-5807ddd72ab2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a287b2f0-8684-4345-9f02-873de6f478fd]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a287b2f0-8684-4345-9f02-873de6f478fd
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
statistics          : {collisions=0, rx_bytes=1372809955, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=83975922, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8458216c-76a1-4cd4-b3da-3682d6ddbdb8
admin_state         : down
ifindex             : 65
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 1ffe157c-9b78-46d5-a87f-b121fd385680
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2101509000, tx_dropped=0, tx_errors=0, tx_packets=1401006}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a20a782f-fc63-413e-b2df-66e8a5bb9de2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=984004104, tx_dropped=0, tx_errors=0, tx_packets=49342961}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 105a9298e9aadf99fdf1a8943f9397f2a7cf11d6
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Tue Aug 5 13:51:19 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Tue Aug 5 13:51:19 2014 -0700

    lib/ovs-atomic: Native support for 32-bit 586 with GCC.
    
    XenServer runs OVS in dom0, which is a 32-bit VM.  As the build
    environment lacks support for atomics, locked pthread atomics were
    used with considerable performance hit.
    
    This patch adds native support for ovs-atomic with 32-bit Pentium and
    higher CPUs, when compiled with an older GCC.  We use inline asm with
    the cmpxchg8b instruction, which was a new instruction to Intel
    Pentium processors.  We do not expect anyone to run OVS on 486 or older
    processor.
    
    cmap benchmark before the patch on 32-bit XenServer build &#40;uses
    ovs-atomic-pthread&#41;:
    
    $ tests/ovstest test-cmap benchmark 2000000 8 0.1
    Benchmarking with n=2000000, 8 threads, 0.10% mutations:
    cmap insert:   8835 ms
    cmap iterate:   379 ms
    cmap search:   6242 ms
    cmap destroy:  1145 ms
    
    After:
    
    $ tests/ovstest test-cmap benchmark 2000000 8 0.1
    Benchmarking with n=2000000, 8 threads, 0.10% mutations:
    cmap insert:    711 ms
    cmap iterate:    68 ms
    cmap search:    353 ms
    cmap destroy:   209 ms
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
