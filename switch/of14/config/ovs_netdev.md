---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a4d1406a-e07a-4e37-9662-ccab6bf94fd2
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 5f447598-0e66-4f07-ac3e-10173e259647
controller          : [253f2b0b-c5e7-4ee4-9c37-1b7995853dc4]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [274deb43-ccd5-47c9-91ff-7272ec9a986f, 3cda4120-68db-4539-a75b-4cd97be56eb2, 72660283-3e59-448d-9891-9613b6b3485b, e0e7d817-97c4-44c4-9f0d-b562c15c5f50]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 253f2b0b-c5e7-4ee4-9c37-1b7995853dc4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=677, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3cda4120-68db-4539-a75b-4cd97be56eb2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ae9d39c5-045f-4dcd-a763-c960138d8a29]
name                : eth21

_uuid               : e0e7d817-97c4-44c4-9f0d-b562c15c5f50
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [21c50a77-bce7-481b-b980-730cf55d8d0b]
name                : eth23

_uuid               : 72660283-3e59-448d-9891-9613b6b3485b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fdf2e9fd-14eb-4ae4-8bea-c9605a477cd5]
name                : br0

_uuid               : 274deb43-ccd5-47c9-91ff-7272ec9a986f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [02e44328-fbce-4af4-b25f-3f96c404aba7]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 02e44328-fbce-4af4-b25f-3f96c404aba7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=157946889872, tx_dropped=0, tx_errors=0, tx_packets=105344779}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : fdf2e9fd-14eb-4ae4-8bea-c9605a477cd5
admin_state         : down
duplex              : full
ifindex             : 305
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

_uuid               : ae9d39c5-045f-4dcd-a763-c960138d8a29
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
statistics          : {collisions=0, rx_bytes=257501047221, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=171771037, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 21c50a77-bce7-481b-b980-730cf55d8d0b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=13507753500, tx_dropped=0, tx_errors=0, tx_packets=9005169}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fa373af463a1421a1b55539911abf33a847bc9b1
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Oct 30 10:38:06 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Oct 30 12:47:01 2014 -0700

    netdev-linux: Avoid depending on kernel definition of rtnl_link_stats64.
    
    We have to define our own with some kernel headers, so we might as well do
    it everywhere, especially since there seems to be a problem with detecting
    the presence of the definition with at least some kernels.
    
    Reported-by: Wang Sheng-Hui &lt;shhuiw@gmail.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
