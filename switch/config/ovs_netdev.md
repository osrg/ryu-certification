---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2a33a902-04b0-4b03-a48e-0769df07ecb4
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
_uuid               : 26868fa1-3fa2-4ef9-bd9c-29810029db16
controller          : [31dffb61-45e3-4c96-b51c-f41329a08aec]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0e4e80b3-ec78-4c8f-95ff-2c72e84e6d69, 8034cecb-4d28-4f73-a259-fa621464d2ee, 959fbbfa-8b44-4f5a-8bae-7d2d97d39669, dcbb1f75-cd79-4973-a254-39b19b792729]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 31dffb61-45e3-4c96-b51c-f41329a08aec
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=966, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : dcbb1f75-cd79-4973-a254-39b19b792729
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [86664019-dc25-4a58-8f6d-ff5201fd7aab]
name                : eth22

_uuid               : 959fbbfa-8b44-4f5a-8bae-7d2d97d39669
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9800a92f-4c56-455c-844d-cf35b5e0ff29]
name                : eth23

_uuid               : 8034cecb-4d28-4f73-a259-fa621464d2ee
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [145e1517-77bf-4404-a7c5-1df50ac6d865]
name                : br0

_uuid               : 0e4e80b3-ec78-4c8f-95ff-2c72e84e6d69
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [43124dcb-f48a-48d0-825c-a8ae6cd66021]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 86664019-dc25-4a58-8f6d-ff5201fd7aab
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2334128624, tx_dropped=0, tx_errors=0, tx_packets=13038593}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 145e1517-77bf-4404-a7c5-1df50ac6d865
admin_state         : down
duplex              : full
ifindex             : 491
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

_uuid               : 43124dcb-f48a-48d0-825c-a8ae6cd66021
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
statistics          : {collisions=0, rx_bytes=2898698488, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27781066, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9800a92f-4c56-455c-844d-cf35b5e0ff29
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3310399408, tx_dropped=0, tx_errors=0, tx_packets=7933556}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 31125ebd8f9b946dc69baadb0f4b2043760e5f6e
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Tue Jun 10 10:38:33 2014 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Fri Jun 13 12:09:47 2014 -0700

    lisp: Use IP addresses rather than flow on hash failure.
    
    When calculating the source port for the UDP header, LISP primarily
    uses skb_get_hash&#40;&#41; but needs a backup in case this fails. The
    current backup is a hash of the entire flow key but this includes
    many fields that probably would not be considered to be part of a
    flow in many situations. It assumes that all fields, including those
    not used, are zeroed out which will soon not be the case.
    
    This switches to using a hash of the IP addresses instead, which
    solves both problems. These should always be present since LISP
    encapsulates L3 packets.
    
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Thomas Graf &lt;tgraf@suug.ch&gt;
</pre>
