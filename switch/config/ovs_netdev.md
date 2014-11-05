---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4960f8d9-3c8d-4b91-950f-898445849ee2
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
_uuid               : e5d6ce28-f961-4b19-915d-f2fed33f1170
controller          : [f603205d-4071-4dea-8d1f-a06352a3bdcd]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4037a684-d65d-489d-a211-6eca966e484b, 5ada50c7-1de8-4b90-8d1e-073b7b78b8d0, 84b40299-6224-4276-8b54-c84042f3a3b3, d0d1aa92-acf4-47ee-8167-38c63664cbd9]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f603205d-4071-4dea-8d1f-a06352a3bdcd
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=682, sec_since_disconnect=6, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4037a684-d65d-489d-a211-6eca966e484b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [08bb133a-fb32-4552-a590-efd032f929c7]
name                : eth23

_uuid               : 84b40299-6224-4276-8b54-c84042f3a3b3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [084b7061-ef30-4772-9708-25c6252e65f4]
name                : eth21

_uuid               : d0d1aa92-acf4-47ee-8167-38c63664cbd9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5297af87-69e8-4889-a6a5-50ff9f5041e0]
name                : br0

_uuid               : 5ada50c7-1de8-4b90-8d1e-073b7b78b8d0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a4b6e3eb-e267-4fe9-8e0b-88f69c95071f]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 084b7061-ef30-4772-9708-25c6252e65f4
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
statistics          : {collisions=0, rx_bytes=271221745215, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=180926070, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 08bb133a-fb32-4552-a590-efd032f929c7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=14469451500, tx_dropped=0, tx_errors=0, tx_packets=9646301}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 5297af87-69e8-4889-a6a5-50ff9f5041e0
admin_state         : down
duplex              : full
ifindex             : 325
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

_uuid               : a4b6e3eb-e267-4fe9-8e0b-88f69c95071f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=160778554232, tx_dropped=0, tx_errors=0, tx_packets=107236041}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5167d6b010082d0a164fd743800fe653bbb310d2
Author:     Eitan Eliahu &lt;eliahue@vmware.com&gt;
AuthorDate: Wed Nov 5 01:39:20 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Nov 5 07:28:23 2014 -0800

    router-table-stub: Fix compilation error.
    
    Signed-off-by: Eitan Eliahu &lt;eliahue@vmware.com&gt;
    Acked-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
