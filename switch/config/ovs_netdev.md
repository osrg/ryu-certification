---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2643171a-2100-460d-8976-cc721ffa5b9f
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
_uuid               : 2f049840-fa7c-49ad-85d0-f9288fa2722a
controller          : [6d3d7aa2-9a44-42c7-ac78-6cc509544ae8]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1d7ca50e-dc24-429b-b6c1-27ad83b05891, 7e9747eb-419f-434f-918a-c69d6fac65ca, b04fe7d4-7070-4838-8866-5ed5c4210c5e, e5d295b6-bca8-48b1-b760-ab4bfe16ee21]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6d3d7aa2-9a44-42c7-ac78-6cc509544ae8
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=677, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b04fe7d4-7070-4838-8866-5ed5c4210c5e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [584e39f6-61c1-4e8e-9ded-e2dbffe1a38e]
name                : br0

_uuid               : 1d7ca50e-dc24-429b-b6c1-27ad83b05891
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aa24e565-eade-478d-83bd-444682034bd0]
name                : eth21

_uuid               : e5d295b6-bca8-48b1-b760-ab4bfe16ee21
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9c9fbed4-3a4b-4e6b-bce7-b8dc37f5304d]
name                : eth23

_uuid               : 7e9747eb-419f-434f-918a-c69d6fac65ca
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [902ffe69-dffb-4783-8091-5a294d0f1342]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9c9fbed4-3a4b-4e6b-bce7-b8dc37f5304d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4142921204, tx_dropped=0, tx_errors=0, tx_packets=5625259}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 902ffe69-dffb-4783-8091-5a294d0f1342
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3318166688, tx_dropped=0, tx_errors=0, tx_packets=48053480}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : aa24e565-eade-478d-83bd-444682034bd0
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
statistics          : {collisions=0, rx_bytes=2466576275, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=76152976, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 584e39f6-61c1-4e8e-9ded-e2dbffe1a38e
admin_state         : down
duplex              : full
ifindex             : 202
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5eca22a2a7fb1fe035316db45d86ee804ec88a55
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Wed Oct 1 21:59:16 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Thu Oct 2 23:12:49 2014 -0700

    bfd.at: Fix intermittent failure of test - flap_count.
    
    ovs-vsctl commands like 'ovs-vsctl list Interface p1' use the
    'monitor' RPC method, which causes ovsdb sending updates to
    the command session when changes are committed to the monitored
    table.  Since ovs-vsctl commands are short-lived, there is chance
    that ovs-vsctl terminates the connection to ovsdb right before
    ovsdb sends the update.  This race will cause the following
    warning entries in ovsdb-server log:
    
      |jsonrpc|WARN|unix: receive error: Connection reset by peer
      |reconnect|WARN|unix: connection dropped &#40;Connection reset by peer&#41;
      |jsonrpc|WARN|unix: send error: Broken pipe
      |reconnect|WARN|unix: connection dropped &#40;Broken pipe&#41;
    
    The bfd:flap_count test is particularly prone to this race,
    since the test aligns the statistics updates &#40;every 5 seconds&#41;
    with the invocation of ovs-vsctl commands.
    
    In the short term, this commit fixes the intermittent failure
    by disabling the ovs-vswitchd statistics updates using a huge
    update interval.
    
    In the long run, we will research on making ovsdb not send
    further updates to sessions like ovs-vsctl.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
