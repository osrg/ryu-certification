---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
14521581-6116-4bcc-8796-fcd4d37b616a
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
_uuid               : 6235a387-ec25-441c-8c9c-6da0380c771b
controller          : [5dd34be7-d77c-4f04-ba81-17603d44ff5e]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1b82a03a-3e39-40d7-b727-24a01c0f8cdd, 6221d2aa-abd2-49c2-8a6d-f3bdaf33f983, b1dbf85c-9b31-488c-8faf-3476ccbcd6f9, f7010e38-d9b6-4e68-b020-427161a8cefc]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5dd34be7-d77c-4f04-ba81-17603d44ff5e
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=977, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b1dbf85c-9b31-488c-8faf-3476ccbcd6f9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [12514c53-24bd-47e8-8e7f-3ba6f29788da]
name                : br0

_uuid               : f7010e38-d9b6-4e68-b020-427161a8cefc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [52e64308-dc35-43b5-bd8c-c3f27e954569]
name                : eth22

_uuid               : 6221d2aa-abd2-49c2-8a6d-f3bdaf33f983
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7df52868-a393-4d50-9313-24b831b3d9e9]
name                : eth23

_uuid               : 1b82a03a-3e39-40d7-b727-24a01c0f8cdd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [73d4e79e-6943-44d8-bfac-71998d66507a]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 52e64308-dc35-43b5-bd8c-c3f27e954569
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2026612602, tx_dropped=0, tx_errors=0, tx_packets=12832002}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 7df52868-a393-4d50-9313-24b831b3d9e9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2659696408, tx_dropped=0, tx_errors=0, tx_packets=7499754}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 73d4e79e-6943-44d8-bfac-71998d66507a
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
statistics          : {collisions=0, rx_bytes=2080573418, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27231506, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 12514c53-24bd-47e8-8e7f-3ba6f29788da
admin_state         : down
duplex              : full
ifindex             : 470
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
