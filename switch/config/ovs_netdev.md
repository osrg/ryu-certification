---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
380ba6d8-520f-47a4-8cb5-60931f340373
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d80f9572-364d-41e4-96fe-f5eb8a95ae74
controller          : [46247820-93d6-49dc-bbf6-e26b0d864aea]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [17700372-f6f5-4700-95b7-370451673462, 179b6839-3a48-4fcb-a084-79dfd226d150, 590ffe8a-0012-48c7-adab-afa3f6bfb842, fb25200f-eed5-492c-b5e2-44825ccff091]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 46247820-93d6-49dc-bbf6-e26b0d864aea
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=821, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 179b6839-3a48-4fcb-a084-79dfd226d150
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d4d2deaa-3804-45be-83da-0a6eb4784287]
name                : eth21

_uuid               : 17700372-f6f5-4700-95b7-370451673462
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [918e88ad-45ca-48cd-8bde-ea53b0a9db31]
name                : eth23

_uuid               : 590ffe8a-0012-48c7-adab-afa3f6bfb842
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [29cfd436-1aa1-49a8-b0c5-84845db362bd]
name                : br0

_uuid               : fb25200f-eed5-492c-b5e2-44825ccff091
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0a733a74-b98f-409d-bde3-cda704252fe8]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0a733a74-b98f-409d-bde3-cda704252fe8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2518961532, tx_dropped=0, tx_errors=0, tx_packets=104801170}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 918e88ad-45ca-48cd-8bde-ea53b0a9db31
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3651077908, tx_dropped=0, tx_errors=0, tx_packets=8160675}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 29cfd436-1aa1-49a8-b0c5-84845db362bd
admin_state         : down
duplex              : full
ifindex             : 277
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

_uuid               : d4d2deaa-3804-45be-83da-0a6eb4784287
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
statistics          : {collisions=0, rx_bytes=2367939577, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=170608656, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit b7cefbf7e52eb0262adb8447409d6ee52eb68a59
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Wed Oct 22 15:35:18 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Thu Oct 23 11:07:32 2014 -0700

    stream-tcp: Call setsockopt TCP_NODELAY after TCP is connected.
    
    On Windows platform, TCP_NODELAY can only be set when TCP is established.
    &#40;This is an observed behavior and not written in any MSDN documentation.&#41;
    The current code does not create any problems while running unit tests
    &#40;because connections get established immediately&#41; but is reportedly
    observed while connecting to a different machine.
    
    commit 8b76839&#40;Move setsockopt TCP_NODELAY to when TCP is connected.&#41;
    made changes to call setsockopt with TCP_NODELAY after TCP is connected
    only in lib/stream-ssl.c. We need the same change for stream-tcp too and
    this commit does that.
    
    Currently, a failure of setting TCP_NODELAY results in reporting
    the error and then closing the socket. This commit changes that
    behavior such that an error is reported if setting TCP_NODELAY
    fails, but the connection itself is not torn down.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
