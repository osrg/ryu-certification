---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
048f1ae3-da87-49f0-b132-fd717f797a1e
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 55f09ef9-c33b-4539-b6a3-6bc397d3ffcd
controller          : [797360e5-f185-4162-a501-b25375e09730]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [02023c3d-d040-4150-a2ac-fbeecd2e9a5c, 105c0082-23dd-4828-a133-5005f5a6339e, 7946f61f-6752-4bb5-9bb5-7cb45897d8cb, ff22634f-ab17-4542-ba2c-5edf122ba07b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 797360e5-f185-4162-a501-b25375e09730
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=566, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 02023c3d-d040-4150-a2ac-fbeecd2e9a5c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [53b6b6cd-d574-43f1-ac3b-d894518921b3]
name                : eth23

_uuid               : 105c0082-23dd-4828-a133-5005f5a6339e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6a12787c-27cc-4d8f-ac82-b733e346f1c6]
name                : br0

_uuid               : 7946f61f-6752-4bb5-9bb5-7cb45897d8cb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8b973b77-e707-46e7-9b90-18a2bace120e]
name                : eth21

_uuid               : ff22634f-ab17-4542-ba2c-5edf122ba07b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5f625445-49c0-41d8-b285-e5b864fae242]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6a12787c-27cc-4d8f-ac82-b733e346f1c6
admin_state         : down
duplex              : full
ifindex             : 1143
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

_uuid               : 53b6b6cd-d574-43f1-ac3b-d894518921b3
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1500
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1601190000, tx_dropped=0, tx_errors=0, tx_packets=1067460}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 5f625445-49c0-41d8-b285-e5b864fae242
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1500
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1861914926, tx_dropped=0, tx_errors=0, tx_packets=1248225}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8b973b77-e707-46e7-9b90-18a2bace120e
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=3120605719, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2097655, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 83709dfafba5b8b58670cec4a2e95204ef63e6e2
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Thu Apr 24 08:21:49 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Thu Apr 24 08:27:58 2014 -0700

    ofproto: Reduce taking rule references.
    
    Only take reference to a looked up rule when needed.
    
    This reduces the total CPU utilization of rule_ref/unref calls by 80%,
    from 5% of total server CPU capacity to 1% in a netperf TCP_CRR
    test stressing the userspace.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
