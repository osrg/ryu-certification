---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1fa4d0f3-82f0-430e-b0b0-f452934b6cef
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 9440f873-dbbf-4ba1-8475-fc7526fd7eae
controller          : [e21a0234-0c73-414b-940d-53c6bf7a7be2]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [835da252-95b0-49bd-ad75-b0aa7c5dda23, bea06c87-a2aa-49cd-8e8c-e38df0574a4a, e5c4cfb8-23c0-43e0-b082-81b19f450f6f, f424b052-9dbe-40b0-a5ab-ced2a8424eb4]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e21a0234-0c73-414b-940d-53c6bf7a7be2
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=727, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e5c4cfb8-23c0-43e0-b082-81b19f450f6f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b5508311-98fb-41fe-ae2b-1169b20e3dea]
name                : eth22

_uuid               : f424b052-9dbe-40b0-a5ab-ced2a8424eb4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aa2f5a6e-e835-4504-a45d-752b16478e7c]
name                : br0

_uuid               : 835da252-95b0-49bd-ad75-b0aa7c5dda23
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d88bec99-e674-4520-92e2-f8249ae5f518]
name                : eth21

_uuid               : bea06c87-a2aa-49cd-8e8c-e38df0574a4a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c7586198-00f4-4e29-8cd6-5d0943ba1329]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c7586198-00f4-4e29-8cd6-5d0943ba1329
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3018141000, tx_dropped=0, tx_errors=0, tx_packets=2012094}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b5508311-98fb-41fe-ae2b-1169b20e3dea
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1047678644, tx_dropped=0, tx_errors=0, tx_packets=23614742}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d88bec99-e674-4520-92e2-f8249ae5f518
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
statistics          : {collisions=0, rx_bytes=2403859608, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=33120769, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : aa2f5a6e-e835-4504-a45d-752b16478e7c
admin_state         : down
duplex              : full
ifindex             : 85
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
commit b1bf47f2251507f45d0c333314501c51207701aa
Author:     Eitan Eliahu &lt;eliahue@vmware.com&gt;
AuthorDate: Tue Sep 2 19:11:13 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Sep 2 11:36:44 2014 -0700

    getopt_long: Fix broken sequence of casts in __UNCONST macor.
    
    Unlike the compilation mode used for OVS x64 Linux Windows long word is
    4 bytes for both 32 and 64 bit builds.
    Replaced _UNCONST macro with CONST_CAST to avoid the intermediate casting
    to an integer.
    
    Testing: 32 and 64 Windows builds.
    Signed-off-by: Eitan Eliahu eliahue@vmware.com
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
