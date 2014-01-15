---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
caa2fc81-9121-4b51-aefd-20ff426480c4
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 5b87c8dd-5411-48fe-ba6c-b7717dcaa071
controller          : [775d862c-280e-487b-9b5b-d54fdd3e647a]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [32eb9ed5-e1b3-4c92-94f4-f330cfc4e9ff, 9b883bd7-c4b0-47a0-b8df-7a4f11541a3b, d2493b40-8b2b-4414-8d99-945ec507156b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 775d862c-280e-487b-9b5b-d54fdd3e647a
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=301, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d2493b40-8b2b-4414-8d99-945ec507156b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2ce070a9-2830-45e3-bbcc-dbb32d21442a]
name                : eth8

_uuid               : 32eb9ed5-e1b3-4c92-94f4-f330cfc4e9ff
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [07abf18c-d06b-440a-908a-31209a2c975e]
name                : br0

_uuid               : 9b883bd7-c4b0-47a0-b8df-7a4f11541a3b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [74472897-b894-4340-8854-95336fb4e1d2]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 07abf18c-d06b-440a-908a-31209a2c975e
admin_state         : up
duplex              : full
ifindex             : 73
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 2ce070a9-2830-45e3-bbcc-dbb32d21442a
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=469592, tx_dropped=0, tx_errors=0, tx_packets=5060}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 74472897-b894-4340-8854-95336fb4e1d2
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=1501095, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=15180, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e491a67a00053471300dd7ef6466bb66ff68de3b
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Wed Jan 15 10:06:40 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jan 15 10:08:40 2014 -0800

    ofproto-dpif-xlate: Avoid recursive acquisition of xlate_rwlock.
    
    Currently xlate_rwlock is recursively acquired.
    (xlate_send_packet -&gt; ofproto_dpif_execute_actions -&gt; xlate_actions)
    Due to writer-preference in rwlock implementations, this causes
    deadlock if another thread tries to acquire the lock exclusively
    behind us.
    
    This change avoids the problem by making xlate_send_packet drop
    the lock before calling ofproto_dpif_execute_actions.  This is the
    simplest fix but opens a race window against port reconfigurations.
    Given the way xlate_send_packet is currently used, the race does not
    seem a big problem.  An alternative would be passing down the
    xlate_rwlock is held info to ofproto_dpif_execute_actions.
    
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
