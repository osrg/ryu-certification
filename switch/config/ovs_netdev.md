---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9adc1d46-8bb9-4e1f-a45d-8fc6cc192460
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a6a03034-454d-41c7-a4ed-049ea6406143
controller          : [19baa6e0-fc65-4754-9117-ef6f2a91b3c4]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0a290dc1-38f1-4ce7-9ba6-fdca356c009e, 0b0c293d-17c4-4fed-a0b0-c65afb821b25, 459fd168-1f32-4f2c-a0c0-5fa103eaa4ed, 7c844bca-a922-4e43-9d75-0a399c0cd5c7]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 19baa6e0-fc65-4754-9117-ef6f2a91b3c4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=682, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 459fd168-1f32-4f2c-a0c0-5fa103eaa4ed
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [74256bfe-bfbd-4199-b31c-73bb858fa02f]
name                : eth21

_uuid               : 0b0c293d-17c4-4fed-a0b0-c65afb821b25
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [01f2dead-2811-42ef-b230-b408c868c2bf]
name                : eth23

_uuid               : 0a290dc1-38f1-4ce7-9ba6-fdca356c009e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c34991bb-44fc-49dd-af00-75a146120061]
name                : br0

_uuid               : 7c844bca-a922-4e43-9d75-0a399c0cd5c7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c05b5d75-b6eb-4bd1-8824-f24f3b6fe1cc]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 01f2dead-2811-42ef-b230-b408c868c2bf
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=13992400500, tx_dropped=0, tx_errors=0, tx_packets=9328267}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c05b5d75-b6eb-4bd1-8824-f24f3b6fe1cc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=160442207988, tx_dropped=0, tx_errors=0, tx_packets=107010241}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 74256bfe-bfbd-4199-b31c-73bb858fa02f
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
statistics          : {collisions=0, rx_bytes=270543850407, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=180470798, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c34991bb-44fc-49dd-af00-75a146120061
admin_state         : down
duplex              : full
ifindex             : 315
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
commit bd8bf90f721bef30a819d0eddd7daa0f1dd64007
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Fri Oct 31 16:47:45 2014 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Mon Nov 3 07:00:05 2014 -0800

    packets: Use WORDS_BIGENDIAN for struct geneve_opt.
    
    The macro LITTLE_ENDIAN is a constant, not a test for endianness,
    so it doesn't actually tell us anything about the machine.
    WORDS_BIGENDIAN is both correct and defined by configure so it is
    more portable.
    
    Reported-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
