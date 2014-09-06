---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0f12e0d2-46e0-4180-8727-301f73a03a5b
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d5ae3114-96d0-4cee-92fd-b978ec6dc178
controller          : [7f2f4184-fc45-491b-853e-33ae16479211]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [350ef9e5-9584-4b4c-91f9-73646fc1ca75, 5e5b3720-03ba-4754-ade7-224bbfd2891a, ecc17565-3eb5-4438-a57b-48133d38d159, f4937b48-d407-4ec8-80e0-4807b51646ce]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7f2f4184-fc45-491b-853e-33ae16479211
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=667, sec_since_disconnect=6, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5e5b3720-03ba-4754-ade7-224bbfd2891a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9e6e1723-4b51-4a9d-b4a2-aeca90b2e3da]
name                : eth22

_uuid               : f4937b48-d407-4ec8-80e0-4807b51646ce
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [435f6866-6094-4287-b6dd-b4d9da57e040]
name                : br0

_uuid               : ecc17565-3eb5-4438-a57b-48133d38d159
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6d6d2f26-82c4-4192-93b3-6dd0ff4582f1]
name                : eth21

_uuid               : 350ef9e5-9584-4b4c-91f9-73646fc1ca75
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cffdcfc2-fc93-417d-a493-dce2003c0c63]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6d6d2f26-82c4-4192-93b3-6dd0ff4582f1
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
statistics          : {collisions=0, rx_bytes=3432549324, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=33811781, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : cffdcfc2-fc93-417d-a493-dce2003c0c63
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3758476500, tx_dropped=0, tx_errors=0, tx_packets=2505651}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 435f6866-6094-4287-b6dd-b4d9da57e040
admin_state         : down
duplex              : full
ifindex             : 101
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

_uuid               : 9e6e1723-4b51-4a9d-b4a2-aeca90b2e3da
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1541659286, tx_dropped=0, tx_errors=0, tx_packets=23946500}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 2c8c4fb7ff82f20cf742bea0625003a8eb428241
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Mon Aug 11 00:14:05 2014 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Fri Sep 5 17:34:40 2014 -0700

    datapath: Implement recirc action without recursion
    
    Since kernel stack is limited in size, it is not wise to using
    recursive function with large stack frames.
    
    This patch provides an alternative implementation of recirc action
    without using recursion.
    
    A per CPU fixed sized, 'deferred action FIFO', is used to store either
    recirc or sample actions encountered during execution of an action
    list. Not executing recirc or sample action in place, but rather execute
    them laster as 'deferred actions' avoids recursion.
    
    Deferred actions are only executed after all other actions has been
    executed, including the ones triggered by loopback from the kernel
    network stack.
    
    The size of the private FIFO, currently set to 20, limits the number
    of total 'deferred actions' any one packet can accumulate.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
