---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b55b46cf-82fe-439c-a558-31739fb44419
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 01fd291d-1bcc-4e99-82db-3ac5cc3a4393
controller          : [3160c9b1-5e98-40af-8ea1-5202504c8651]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [25bdf20b-5d3a-4ab9-ac71-cdc41e5a8933, 60f4815d-bc67-42ba-9700-08151b07faa5, 6fddec94-daad-44fb-b10e-9c6727a21b48]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3160c9b1-5e98-40af-8ea1-5202504c8651
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=371, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6fddec94-daad-44fb-b10e-9c6727a21b48
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ff93e525-5d53-4cd4-9be4-4e83f01c215c]
name                : br0

_uuid               : 60f4815d-bc67-42ba-9700-08151b07faa5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bae339c9-c19e-45d5-91fd-0ca1f7cb4c3e]
name                : eth7

_uuid               : 25bdf20b-5d3a-4ab9-ac71-cdc41e5a8933
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e09d3cf0-95ba-4153-b65e-11432f158f91]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e09d3cf0-95ba-4153-b65e-11432f158f91
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3910222, tx_dropped=0, tx_errors=0, tx_packets=41711}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : bae339c9-c19e-45d5-91fd-0ca1f7cb4c3e
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
statistics          : {collisions=0, rx_bytes=3063946330, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72642188, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : ff93e525-5d53-4cd4-9be4-4e83f01c215c
admin_state         : up
duplex              : full
ifindex             : 527
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit cc7a9de0a5b52ae2b8161e5d8c9d51c61f849102
Author:     Alexandru Copot &lt;alex.mihai.c@gmail.com&gt;
AuthorDate: Thu Mar 13 22:08:48 2014 +0200
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Sat Mar 15 09:28:44 2014 -0700

    openflow-1.4.h: Add bundle structure definitions
    
    Signed-off-by: Alexandru Copot &lt;alex.mihai.c@gmail.com&gt;
    Cc: Daniel Baluta &lt;dbaluta@ixiacom.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
