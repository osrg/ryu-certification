---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
cf087461-79d1-49ab-9227-58261f9a6482
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e1f238fc-31ef-4af9-8660-f80a22a715c3
controller          : [b121c2ef-b5ed-454a-8f18-385b8c5a7bcc]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [6704ca82-46ba-4578-9fa3-565fea851646, 9536a279-eb48-4a0d-8920-9b57cfa6a3f5, 9a76a8e7-2a27-45e4-b369-1eefb9a66c19, 9ea6ecd6-40de-4267-a6a3-553450336725]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b121c2ef-b5ed-454a-8f18-385b8c5a7bcc
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=972, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9536a279-eb48-4a0d-8920-9b57cfa6a3f5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [46d48d0d-2450-4817-bfe1-38a2d7d8360e]
name                : br0

_uuid               : 9ea6ecd6-40de-4267-a6a3-553450336725
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [081ab4b9-5638-4002-b3c6-7653d8619644]
name                : eth22

_uuid               : 6704ca82-46ba-4578-9fa3-565fea851646
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c81b522b-7448-4915-a4ba-920920cae993]
name                : eth21

_uuid               : 9a76a8e7-2a27-45e4-b369-1eefb9a66c19
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [90a355f3-5302-4eb8-9b6f-d08632bcdd5c]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 081ab4b9-5638-4002-b3c6-7653d8619644
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1318703826, tx_dropped=0, tx_errors=0, tx_packets=35285117}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 46d48d0d-2450-4817-bfe1-38a2d7d8360e
admin_state         : down
duplex              : full
ifindex             : 643
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

_uuid               : 90a355f3-5302-4eb8-9b6f-d08632bcdd5c
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=3663351580, tx_dropped=0, tx_errors=0, tx_packets=11032853}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c81b522b-7448-4915-a4ba-920920cae993
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
statistics          : {collisions=0, rx_bytes=894492205, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=89478832, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 42165119992397504f409390003e143225ca59a4
Author:     Pim van den Berg &lt;pim@nethuis.nl&gt;
AuthorDate: Sat Jun 21 11:59:52 2014 +0200
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Jun 24 11:21:29 2014 -0700

    utilities: skip loading kernel module if kernel has no module support
    
    Signed-off-by: Pim van den Berg &lt;pim@nethuis.nl&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
