---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
78dd251d-2fef-4895-9a4e-72139796dd3d
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 97d3f87e-2210-4425-9d0f-15b846e7b15f
controller          : [2354baee-aab9-4043-a2c9-bb19334a9858]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [879f9b1b-0acc-49b5-8c57-55aa41a33054, b6579bdf-16b3-49fb-bda9-bf78505c17bb, bd3f586d-1f47-41fd-a0d5-e98f66cc207e, c6e86a4f-e8b6-4330-92d8-d561a253d4ea]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2354baee-aab9-4043-a2c9-bb19334a9858
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=556, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : bd3f586d-1f47-41fd-a0d5-e98f66cc207e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7f9ffc0b-955a-4b48-92cd-1eb55b59b345]
name                : eth22

_uuid               : c6e86a4f-e8b6-4330-92d8-d561a253d4ea
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [57e1beac-9c97-457f-b6a5-c58e47501ba2]
name                : eth21

_uuid               : b6579bdf-16b3-49fb-bda9-bf78505c17bb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6c429983-764b-43ae-97c0-dd60b68623ef]
name                : br0

_uuid               : 879f9b1b-0acc-49b5-8c57-55aa41a33054
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5d1d93b7-ce7e-4609-ae8c-6c582e330290]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 57e1beac-9c97-457f-b6a5-c58e47501ba2
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
statistics          : {collisions=0, rx_bytes=561058698, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=375919, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 7f9ffc0b-955a-4b48-92cd-1eb55b59b345
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=192332526, tx_dropped=0, tx_errors=0, tx_packets=128903}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6c429983-764b-43ae-97c0-dd60b68623ef
admin_state         : down
duplex              : full
ifindex             : 45
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

_uuid               : 5d1d93b7-ce7e-4609-ae8c-6c582e330290
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=438798000, tx_dropped=0, tx_errors=0, tx_packets=292532}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fe83f81df9779ba4fa74111a09764d3153651dac
Author:     Ryan Wilson &lt;wryan@nicira.com&gt;
AuthorDate: Fri May 16 02:17:58 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri May 16 11:35:38 2014 -0700

    netdev: Remove netdev from global shash when the user is changing interface configuration.
    
    When the user changes port type &#40;i.e. changing p0 from type 'internal' to
    'gre'&#41;, the netdev must first be deleted, then re-created with the new type.
    Deleting the netdev requires there exist no more references to the netdev.
    However, the xlate cache holds references to netdevs and the cache is only
    invalidated by revalidator threads. Thus, if cache is not invalidated prior to
    the netdev being re-created, the netdev will not be able to be re-created and
    the configuration change will fail.
    
    This patch always removes the netdev from the global netdev shash when the
    user changes port type. This ensures that the new netdev can always be created
    while handler and revalidator threads can retain references to the old netdev
    until they are finished.
    
    Signed-off-by: Ryan Wilson &lt;wryan@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
