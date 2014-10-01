---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d49e3fe4-11e4-4635-aa1d-81f4c5351038
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 2de051aa-952b-465e-9c69-a899801440ca
controller          : [4325554f-4794-46b4-a243-57036d477695]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5f6871ad-d4ef-49c6-bcd3-0f06a0cb2119, 949256dd-80e1-4571-adf6-7982e916c571, b004981d-c7f9-4ce4-a96c-3a0bd0fb4fae, d867a4b9-881b-44c2-8051-5889314d859f]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4325554f-4794-46b4-a243-57036d477695
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=692, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 949256dd-80e1-4571-adf6-7982e916c571
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4a9da735-02f4-403c-9620-a57d11ae3a00]
name                : eth23

_uuid               : b004981d-c7f9-4ce4-a96c-3a0bd0fb4fae
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1dd39444-a624-42ec-8c39-705146d236d8]
name                : br0

_uuid               : d867a4b9-881b-44c2-8051-5889314d859f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c35c2b95-f488-4bdf-89ce-15299d454981]
name                : eth22

_uuid               : 5f6871ad-d4ef-49c6-bcd3-0f06a0cb2119
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1de137b0-98e9-4b1b-96f8-23f063eb1867]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1de137b0-98e9-4b1b-96f8-23f063eb1867
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
statistics          : {collisions=0, rx_bytes=1893750313, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=75768167, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 1dd39444-a624-42ec-8c39-705146d236d8
admin_state         : down
duplex              : full
ifindex             : 192
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

_uuid               : c35c2b95-f488-4bdf-89ce-15299d454981
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3044902322, tx_dropped=0, tx_errors=0, tx_packets=47869939}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 4a9da735-02f4-403c-9620-a57d11ae3a00
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3728880704, tx_dropped=0, tx_errors=0, tx_packets=5349232}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 538919d3a672eab8a561048acf9a8e1721cd559c
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Sep 30 17:03:07 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Oct 1 08:46:06 2014 -0700

    configure: Disable strict aliasing.
    
    The C standard allows compilers to do type-based alias analysis, which
    means that the compiler is allowed to assume that pointers to objects of
    different types are pointers to different objects.  For example, a compiler
    may assume that &quot;uint16_t *a&quot; and &quot;uint32_t *b&quot; point to different and
    nonoverlapping locations because the pointed-to types are different.  This
    can lead to surprising &quot;optimizations&quot; with compilers that by default do
    this kind of analysis, which includes GCC and Clang.
    
    The one escape clause that the C standard gives us is that character types
    must be assumed to alias any other object.  We've always tried to use this
    escape clause to avoid problems with type-based alias analysis in the past.
    I think that we should continue to try to do this in the future.  It's hard
    to tell what compiler we might want to use in the future, and one never
    knows what kind of control that compiler allows over alias analysis.
    
    However, recently I helped another developer debug a nasty and confusing
    issue, which turned out to be the result of a surprising compiler
    optimization due to alias analysis.  I've seen enough of these that I don't
    think it's worthwhile to risk more problems than we have to.  Thus, this
    commit turns off type-based alias analysis in GCC and Clang.
    
    Linus Torvalds thinks that type-base alias analysis is not sane, at least
    as GCC implements it: https://lkml.org/lkml/2003/2/26/158
    
    The GCC manual says that -Wstrict-aliasing is only effective without
    -fno-strict-aliasing, otherwise I'd keep -Wstrict-aliasing also.
    
    Indications are that MSVC doesn't do type-based alias analysis by default.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
