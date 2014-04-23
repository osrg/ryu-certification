---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7af443f5-d890-4367-bf0b-734fd0f4f704
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f906d13e-d2f3-4c21-9716-c93cedefd2e0
controller          : [c228bc03-6d9a-4ce5-983b-1e7860be3e55]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5c6f8b7b-9f9d-4631-b372-5ab3e7970666, 632c1729-8ae9-4e26-8365-690f17525b42, 9ec235d2-02f6-4b6b-bcdd-3bfe5e99c46a, da6d954e-7734-40c9-8637-1fb103b6c01a]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c228bc03-6d9a-4ce5-983b-1e7860be3e55
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=571, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 632c1729-8ae9-4e26-8365-690f17525b42
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9b9fde5d-2cd3-46de-b6f5-89d9e5df4005]
name                : eth23

_uuid               : 9ec235d2-02f6-4b6b-bcdd-3bfe5e99c46a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [68c43f29-5e84-4039-9d3b-2a19619af178]
name                : eth21

_uuid               : da6d954e-7734-40c9-8637-1fb103b6c01a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b97c598c-4df5-4656-9963-d5f421254819]
name                : br0

_uuid               : 5c6f8b7b-9f9d-4631-b372-5ab3e7970666
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [12797953-9621-43df-a131-fa9a8e6edccc]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b97c598c-4df5-4656-9963-d5f421254819
admin_state         : down
duplex              : full
ifindex             : 1113
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

_uuid               : 9b9fde5d-2cd3-46de-b6f5-89d9e5df4005
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1191142500, tx_dropped=0, tx_errors=0, tx_packets=794095}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 68c43f29-5e84-4039-9d3b-2a19619af178
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
statistics          : {collisions=0, rx_bytes=2369943546, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1593461, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 12797953-9621-43df-a131-fa9a8e6edccc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1427684092, tx_dropped=0, tx_errors=0, tx_packets=957379}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 4c21aa063fa1c7f95800c95fafebedcd577ce674
Author:     Zoltan Kiss &lt;zoltan.kiss@citrix.com&gt;
AuthorDate: Wed Apr 23 14:45:21 2014 +0100
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Apr 23 11:46:55 2014 -0700

    lib/util: Input validation in str_to_uint
    
    This function returns true when 's' is negative or greater than UINT_MAX. Also,
    the representation of 'int' and 'unsigned int' is implementation dependent, so
    converting [INT_MAX..UINT_MAX] values with str_to_int is fragile.
    Instead, we should convert straight to 'long long' and do a boundary check
    before returning the converted value.
    This patch also move the function to the .c file as it's not-trivial now, and
    deletes the other str_to_u* functions as they are not used.
    
    Signed-off-by: Zoltan Kiss &lt;zoltan.kiss@citrix.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
