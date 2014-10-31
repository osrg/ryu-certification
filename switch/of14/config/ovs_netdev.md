---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3e5aaab4-b36f-46c7-8185-628860fc7dad
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
_uuid               : a1b26c6f-3d0e-40b2-bc61-e3084dcf9afb
controller          : [a7fd82d5-77a0-43ca-add9-fafe26a6c8a0]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2f19211f-ec25-4ab6-9b80-5cff53c804b1, 826858cb-a66b-4801-acf3-69c9027d1ecd, 97cd05a6-6b01-4999-aff2-cfd1d1d78df2, f6c2b44c-4bab-462a-b1b6-2cb2c8ba5901]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a7fd82d5-77a0-43ca-add9-fafe26a6c8a0
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=682, sec_since_disconnect=6, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f6c2b44c-4bab-462a-b1b6-2cb2c8ba5901
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [04649043-990a-4eba-b611-3743f202c02a]
name                : eth21

_uuid               : 97cd05a6-6b01-4999-aff2-cfd1d1d78df2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [57cfe462-9460-4f87-b35c-264418d04c64]
name                : eth23

_uuid               : 2f19211f-ec25-4ab6-9b80-5cff53c804b1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8224abde-ea98-4a4e-a5ea-58ec2475d163]
name                : eth22

_uuid               : 826858cb-a66b-4801-acf3-69c9027d1ecd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7995dde8-33ee-4a18-beb9-ed5a2704319a]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7995dde8-33ee-4a18-beb9-ed5a2704319a
admin_state         : down
duplex              : full
ifindex             : 309
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

_uuid               : 8224abde-ea98-4a4e-a5ea-58ec2475d163
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=158052241192, tx_dropped=0, tx_errors=0, tx_packets=105415599}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 57cfe462-9460-4f87-b35c-264418d04c64
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=13682904000, tx_dropped=0, tx_errors=0, tx_packets=9121936}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 04649043-990a-4eba-b611-3743f202c02a
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
statistics          : {collisions=0, rx_bytes=257734817137, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=171928146, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 042d944e72e4c20fa98b7f0d62178115873041c8
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Oct 31 09:49:02 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Oct 31 14:04:51 2014 -0700

    AUTHORS: Add Scott Lowe &lt;scott.lowe@scottlowe.org&gt;.
    
    Contributors to the webpage deserve authorship credit too.
    
    CC: Scott Lowe &lt;scott.lowe@scottlowe.org&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
