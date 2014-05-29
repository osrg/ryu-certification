---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
30fd4d97-2de1-457e-96cf-0601d9487770
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 5df36274-9c8c-4feb-b197-2fe125c45e14
controller          : [c3be6e31-6562-4ce8-a8fc-307df4d8945c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [043cd53d-1219-4f3b-84fd-bb316c2f60d8, c7ec2c2c-3c0e-4e9c-a869-9b177669e394, d4fcd23c-e235-4d4d-a0d0-747245518f87, db75819b-5ab6-4a1c-a4ff-69ece265535f]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c3be6e31-6562-4ce8-a8fc-307df4d8945c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=1617, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c7ec2c2c-3c0e-4e9c-a869-9b177669e394
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [304114f6-f4ad-4e5f-b190-332558276bf0]
name                : eth21

_uuid               : d4fcd23c-e235-4d4d-a0d0-747245518f87
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2b63696a-5570-4406-9323-63b3989898b2]
name                : br0

_uuid               : 043cd53d-1219-4f3b-84fd-bb316c2f60d8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6f378f61-69fa-4568-870c-1a0bd57aa16e]
name                : eth22

_uuid               : db75819b-5ab6-4a1c-a4ff-69ece265535f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f43bd1fd-810d-405c-b2f4-7162f0519352]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f43bd1fd-810d-405c-b2f4-7162f0519352
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2067536204, tx_dropped=0, tx_errors=0, tx_packets=4241669}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6f378f61-69fa-4568-870c-1a0bd57aa16e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3422533892, tx_dropped=0, tx_errors=0, tx_packets=2295106}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2b63696a-5570-4406-9323-63b3989898b2
admin_state         : down
duplex              : full
ifindex             : 280
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

_uuid               : 304114f6-f4ad-4e5f-b190-332558276bf0
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
statistics          : {collisions=0, rx_bytes=4291409786, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=5761017, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0471423a700a643573054b82d820c154c3c839a3
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Thu May 29 16:12:24 2014 +0000
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Thu May 29 09:47:22 2014 -0700

    configure.ac: Check C99 compiler
    
    This ends up to add -std=gnu99 and fixes the following
    compilation problem introduced by commit 08feeb75.
    &#40;&quot;lib/flow: Use C99 declaration in for statement.&quot;&#41;
    
    libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -I ../include -I ../lib -I ./lib -Wstrict-prototypes -Wall -Wextra -Wno-sign-compare -Wpointer-arith -Wno-format-zero-length -Wswitch-enum -Wunused-parameter -Wstrict-aliasing -Wbad-function-cast -Wcast-align -Wmissing-prototypes -Wmissing-field-initializers -g -O2 -MT lib/classifier.lo -MD -MP -MF lib/.deps/classifier.Tpo -c ../lib/classifier.c -o lib/classifier.o
    ../lib/classifier.c: In function 'miniflow_and_mask_matches_flow':
    ../lib/classifier.c:1722:5: error: 'for' loop initial declarations are only allowed in C99 mode
    ../lib/classifier.c:1722:5: note: use option -std=c99 or -std=gnu99 to compile your code
    Makefile:3013: recipe for target 'lib/classifier.lo' failed
    
    % gcc --version
    gcc &#40;NetBSD nb1 20120916&#41; 4.5.4
    Copyright &#40;C&#41; 2010 Free Software Foundation, Inc.
    This is free software; see the source for copying conditions.  There is NO
    warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
    
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
