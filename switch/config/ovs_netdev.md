---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
5ed856dc-b724-4af2-90d1-9b98ca19455c
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
_uuid               : 48d79df8-54ad-4513-a2e6-c51a969f4625
controller          : [16b14721-c5fd-4f20-bcc0-7e089baea9c3]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2230f51b-33ba-4146-8225-81f59c2655d4, 53156ba0-b5e4-439e-992f-0ce7223e2a62, de6a52d9-d2e3-4f2c-bbbd-c1193dd6a9b6, f97b2f80-b9c7-47f5-ad55-195ca904183c]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 16b14721-c5fd-4f20-bcc0-7e089baea9c3
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=972, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 53156ba0-b5e4-439e-992f-0ce7223e2a62
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6ae921ac-9342-47bb-901b-13ec4e0f155b]
name                : eth21

_uuid               : f97b2f80-b9c7-47f5-ad55-195ca904183c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [90205f2e-f349-4923-b92b-85e318f467cf]
name                : eth22

_uuid               : de6a52d9-d2e3-4f2c-bbbd-c1193dd6a9b6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [889e2c8c-4294-48fb-930f-ca02d0c5fa17]
name                : br0

_uuid               : 2230f51b-33ba-4146-8225-81f59c2655d4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [33f9f83c-b834-4832-8cac-fbdf08facc0f]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 889e2c8c-4294-48fb-930f-ca02d0c5fa17
admin_state         : down
duplex              : full
ifindex             : 474
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

_uuid               : 6ae921ac-9342-47bb-901b-13ec4e0f155b
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
statistics          : {collisions=0, rx_bytes=2197495260, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27310080, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 33f9f83c-b834-4832-8cac-fbdf08facc0f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2759245408, tx_dropped=0, tx_errors=0, tx_packets=7566120}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 90205f2e-f349-4923-b92b-85e318f467cf
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2067339472, tx_dropped=0, tx_errors=0, tx_packets=12859386}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 35f48b8bd9b3b3491d79418878ef70dc54b0a8f0
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Jun 5 21:53:34 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jun 12 14:47:22 2014 -0700

    Implement learned flow deletion.
    
    When a flow with a &quot;learn&quot; action is deleted, one often wants the flows
    that it created &#40;the &quot;learned flows&quot;&#41; to be deleted as well.  This commit
    makes that possible.
    
    I am aware of a race condition that could lead to a learned flow not being
    properly deleted.  Suppose thread A deletes a flow with a &quot;learn&quot; action.
    Meanwhile, thread B obtains the actions for this flow and translates and
    executes them.  Thread B could obtain the actions for the flow before it is
    deleted, but execute them after the &quot;learn&quot; flow and its learned flows are
    deleted.  The result is that the flow created by thread B persists despite
    its &quot;learn&quot; flow having been deleted.  This race can and should be fixed,
    but I think that this commit is worth reviewing without it.
    
    VMware-BZ: #1254021
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Thomas Graf &lt;tgraf@suug.ch&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
