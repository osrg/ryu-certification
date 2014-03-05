---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
71d8af05-6007-4dae-bdc0-b6d85bb0a3ad
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 5b200e4a-7f14-403a-8a33-e7bbb5d894f7
controller          : [2372b9d5-af53-4101-a2a9-eca0641a85e6]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [743b0d9d-a541-46e7-b6a2-90f46d6765e0, 908d8fe6-33da-43db-bd02-2a3c74884f68, d1d8c61a-971c-408c-aff9-f9b6ec76a3c8]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2372b9d5-af53-4101-a2a9-eca0641a85e6
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=377, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 743b0d9d-a541-46e7-b6a2-90f46d6765e0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ef07a15b-08dc-4250-a6e3-37fccbc41cf3]
name                : br0

_uuid               : d1d8c61a-971c-408c-aff9-f9b6ec76a3c8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [db4a4c0d-df9a-4ef9-b878-6acd0c39db07]
name                : eth7

_uuid               : 908d8fe6-33da-43db-bd02-2a3c74884f68
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5843d8cb-8251-415a-b984-6ecd04c75ca7]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : db4a4c0d-df9a-4ef9-b878-6acd0c39db07
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
statistics          : {collisions=0, rx_bytes=3061360464, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72615946, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : ef07a15b-08dc-4250-a6e3-37fccbc41cf3
admin_state         : up
duplex              : full
ifindex             : 432
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

_uuid               : 5843d8cb-8251-415a-b984-6ecd04c75ca7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3151410, tx_dropped=0, tx_errors=0, tx_packets=33631}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5020f5f099526ec224ba0b1703806b42ebdaee5a
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Jan 23 15:35:22 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Mar 5 07:51:56 2014 -0800

    Makefile: Compile Linux-specific files based on __linux__ macro.
    
    We want to conditionally compile several files based on whether we're
    building for a Linux host, so we need some Automake conditional for that.
    Previously this was based on whether Netlink is available and we're not
    on ESX (since ESX has Netlink but isn't Linux), but it's more
    straightforward to just test for Linux directly.
    
    CC: Luigi Rizzo &lt;rizzo@iet.unipi.it&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
