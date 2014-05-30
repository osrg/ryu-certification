---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0b97e658-89db-4ac1-bf92-5ca02df6ece1
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : aef41e57-370d-45f3-a921-d785551ab0ad
controller          : [f6b3bf2e-f0d7-4545-99cd-abcb0af52a45]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0486fd88-28e4-4c2a-8fd1-f362e903b63c, 80224fa9-524b-482d-ac0e-5cbfdef6e6d7, 96f7e409-8493-437c-9b0b-ce114d69aff8, d5490d34-964d-4951-aaad-6fcd73527073]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f6b3bf2e-f0d7-4545-99cd-abcb0af52a45
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=1002, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d5490d34-964d-4951-aaad-6fcd73527073
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [036a798e-c4c8-458d-b96a-1431a1f4c4ad]
name                : eth23

_uuid               : 0486fd88-28e4-4c2a-8fd1-f362e903b63c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1085a28b-21ba-483d-9fe9-a011cf2f8add]
name                : eth21

_uuid               : 96f7e409-8493-437c-9b0b-ce114d69aff8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [eb290075-2ab8-4197-847c-44d03bbfbe5f]
name                : eth22

_uuid               : 80224fa9-524b-482d-ac0e-5cbfdef6e6d7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8b3098ba-45ff-4aca-b983-4b5393bfb616]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : eb290075-2ab8-4197-847c-44d03bbfbe5f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3748785428, tx_dropped=0, tx_errors=0, tx_packets=2513964}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 036a798e-c4c8-458d-b96a-1431a1f4c4ad
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2863034204, tx_dropped=0, tx_errors=0, tx_packets=4772001}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8b3098ba-45ff-4aca-b983-4b5393bfb616
admin_state         : down
duplex              : full
ifindex             : 310
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

_uuid               : 1085a28b-21ba-483d-9fe9-a011cf2f8add
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
statistics          : {collisions=0, rx_bytes=931417120, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=6389407, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 8396f8070bb35006fcd14486296fb203646a8dfa
Author:     Ryan Wilson &lt;wryan@nicira.com&gt;
AuthorDate: Fri May 30 15:38:51 2014 -0700
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Fri May 30 15:43:43 2014 -0700

    timeval: Use monotonic time in OVS Python timeval library.
    
    Python's time.time&#40;&#41; function uses the system wall clock. However,
    if NTP resets the wall clock to be a time in the past, then this
    causes any applications that poll block based on time, such as
    ovs-xapi-sync, to poll block indefinitely since the time is
    unexpectedly negative.
    
    This patch fixes the issue by using time.monotonic&#40;&#41; if Python's
    version &gt;= 3.3. Otherwise, the timeval module calls out to the
    librt C shared library and uses the clock_gettime function with
    CLOCK_MONOTONIC.
    
    Note this is only enabled on Linux-based platforms. This has been
    tested on Ubuntu 12.04 and Redhat 6.4.
    
    Bug #1189434
    Signed-off-by: Ryan Wilson &lt;wryan@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
