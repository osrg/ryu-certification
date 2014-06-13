---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9465bca2-ebfa-4c6b-8f28-9d175b924fd0
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 984541da-afb8-453b-a4af-021f8b62da3f
controller          : [7e0d4138-605c-4ed1-9df3-2002baa2fa13]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5fb67aea-ca04-4ac2-9dee-84a4aaf199fd, 90a5d440-2183-4777-925d-73d3b1bc67da, bf54e782-b0d0-457c-b425-3ae0b28fd504, ed076615-6455-4ff6-bfa0-90d49ca52546]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7e0d4138-605c-4ed1-9df3-2002baa2fa13
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=967, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 90a5d440-2183-4777-925d-73d3b1bc67da
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [016da4e7-868f-443f-909b-2336ea489832]
name                : br0

_uuid               : ed076615-6455-4ff6-bfa0-90d49ca52546
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [82d447fd-2a21-4522-9036-b395df3674ef]
name                : eth21

_uuid               : 5fb67aea-ca04-4ac2-9dee-84a4aaf199fd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c39c50f8-61c0-4f0b-a623-3747dcb4e7d4]
name                : eth22

_uuid               : bf54e782-b0d0-457c-b425-3ae0b28fd504
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7e53434e-2cf5-41d0-9bdf-571581077e3f]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c39c50f8-61c0-4f0b-a623-3747dcb4e7d4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2252554884, tx_dropped=0, tx_errors=0, tx_packets=12983745}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 82d447fd-2a21-4522-9036-b395df3674ef
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
statistics          : {collisions=0, rx_bytes=2664962804, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27623990, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 7e53434e-2cf5-41d0-9bdf-571581077e3f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3111535408, tx_dropped=0, tx_errors=0, tx_packets=7800980}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 016da4e7-868f-443f-909b-2336ea489832
admin_state         : down
duplex              : full
ifindex             : 483
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
commit cb220b393ab5c60f0552029a9a642a0813069e50
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Fri Jun 13 11:06:09 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Jun 13 10:44:36 2014 -0700

    ofproto: Initialise return value of modify_flows__
    
    dd51dae29bccca3 &#40;&quot;ofproto: Move logic for collecting read-only rules into
    rule_criteria.&quot;&#41; modifies modify_flows__ such that the variable error,
    the return value, may be uninitialised if either of the following is true:
    
    1. ofproto-&gt;ofproto_class-&gt;rule_premodify_actions is NULL
    2. rules-&gt;n is zero
    
    It appears for the &quot;bfd - Verify tunnel down detection&quot; test
    in the testsuite the first condition is true and the test fails.
    
    This commit fixes the problem.
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    [blp@nicira.com changed the style of the fix]
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
