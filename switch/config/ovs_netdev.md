---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ae59d930-51c0-4219-8f57-2f22ab82c16a
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 80e83848-61ce-45ae-b9ab-6b374708182d
controller          : [665b7671-9a64-42ab-a521-c5e0aa247740]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [644cce5f-13b5-4546-8a87-1fa0ab212de3, 71683828-d102-4146-a3a0-53460fe22261, e94ccd53-24cf-434d-af02-3b49a22682a1, ebcf1a81-8ef7-4994-8b80-2d1b90af4ee5]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 665b7671-9a64-42ab-a521-c5e0aa247740
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=967, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 71683828-d102-4146-a3a0-53460fe22261
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [30ba8ec2-6009-4acc-82c5-dcda747ba5ce]
name                : eth23

_uuid               : ebcf1a81-8ef7-4994-8b80-2d1b90af4ee5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e79ce060-50a3-4a5b-9c86-0571fe2b7d4b]
name                : eth21

_uuid               : 644cce5f-13b5-4546-8a87-1fa0ab212de3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [89045fd0-d054-49e9-9d25-02f7b0d900cf]
name                : br0

_uuid               : e94ccd53-24cf-434d-af02-3b49a22682a1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f1e5dc73-3052-4472-aba5-15091db95937]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e79ce060-50a3-4a5b-9c86-0571fe2b7d4b
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
statistics          : {collisions=0, rx_bytes=545523797, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26199156, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 89045fd0-d054-49e9-9d25-02f7b0d900cf
admin_state         : down
duplex              : full
ifindex             : 432
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

_uuid               : 30ba8ec2-6009-4acc-82c5-dcda747ba5ce
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1615457908, tx_dropped=0, tx_errors=0, tx_packets=6803595}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f1e5dc73-3052-4472-aba5-15091db95937
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1286798798, tx_dropped=0, tx_errors=0, tx_packets=12334961}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 55466d72bd3a3a2bb1f3d1471b063388340e3402
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Fri Jun 6 15:36:14 2014 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Tue Jun 10 15:28:12 2014 -0700

    test: Remove explicit sleeps from ofproto-dpif bond tests
    
    Ofproto-dpif bond tests relies on netdev-dummy ports to set up
    socket connection before actual tests. The time required
    for socket connection varies depends on system load, making the test
    prone to failure with simple sleep calls. On the other hand,
    conservative sleep value for the slowest machine may be excessive on
    a faster machine.
    
    This patch removes the sleep calls. Replace them with
    WAIT_FOR_DUMMY_PORTS&#40;&#41; introduced in the last patch, thus removing
    the timing dependency.
    
    CC: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
