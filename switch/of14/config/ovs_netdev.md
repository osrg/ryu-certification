---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
651178ae-b07b-42bc-98a2-e82a79d94f70
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
_uuid               : cd4a9583-b3d9-403e-86f8-fd263fb426ab
controller          : [9655b9d6-231c-499d-af41-ca3da95a760a]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0e3cc5a5-63a1-4ae0-9241-b5fb0fc7cadd, 121cf416-2209-4fce-a727-f0d0fd7afe60, 41f796bd-c942-44da-af69-0fd2ecc314e6, 4e6c14ce-7510-4c64-bd2b-f47082d77e2e]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9655b9d6-231c-499d-af41-ca3da95a760a
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=661, sec_since_disconnect=7, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0e3cc5a5-63a1-4ae0-9241-b5fb0fc7cadd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b3fb0549-bd03-45c0-bf99-aab8b8c206e1]
name                : eth23

_uuid               : 41f796bd-c942-44da-af69-0fd2ecc314e6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2a273296-ad83-4d91-aed1-c7af11389bb1]
name                : eth21

_uuid               : 4e6c14ce-7510-4c64-bd2b-f47082d77e2e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b045678f-d657-4559-bad0-ebb55780b310]
name                : br0

_uuid               : 121cf416-2209-4fce-a727-f0d0fd7afe60
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f4af33d2-ae8f-4488-9ff0-0c334f27e8eb]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b3fb0549-bd03-45c0-bf99-aab8b8c206e1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3846271500, tx_dropped=0, tx_errors=0, tx_packets=2564181}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f4af33d2-ae8f-4488-9ff0-0c334f27e8eb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1594100946, tx_dropped=0, tx_errors=0, tx_packets=23981754}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2a273296-ad83-4d91-aed1-c7af11389bb1
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
statistics          : {collisions=0, rx_bytes=3549426032, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=33890330, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b045678f-d657-4559-bad0-ebb55780b310
admin_state         : down
duplex              : full
ifindex             : 103
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
