---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
155bf8cb-04ea-4d2b-bf89-4b93f820cc4b
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
_uuid               : 355a921f-49a7-4efb-af8f-9703853475b2
controller          : [2725ddef-f8c3-48b4-9430-39e64bfbd4c1]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0115806d-16ee-4add-b6b2-d72bf7f1df62, 43a440ab-b149-4c75-9b19-644d03c1c1ea, 79cb1c5f-480d-41ec-bd25-69784667f3d5, 85e64f38-d57f-4b1f-a751-869c84f24c0a]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2725ddef-f8c3-48b4-9430-39e64bfbd4c1
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=822, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 85e64f38-d57f-4b1f-a751-869c84f24c0a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9c864218-1978-4571-a9ca-cdab4ccc737f]
name                : eth21

_uuid               : 0115806d-16ee-4add-b6b2-d72bf7f1df62
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [63502553-693e-4479-8476-1562bcad4131]
name                : eth23

_uuid               : 79cb1c5f-480d-41ec-bd25-69784667f3d5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [28a24ee7-429b-4c4e-99cc-a970313ca1fd]
name                : eth22

_uuid               : 43a440ab-b149-4c75-9b19-644d03c1c1ea
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2e54f0da-d5d5-4c18-8a6b-2bfb2e432a85]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9c864218-1978-4571-a9ca-cdab4ccc737f
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
statistics          : {collisions=0, rx_bytes=1327683925, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=169909694, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2e54f0da-d5d5-4c18-8a6b-2bfb2e432a85
admin_state         : down
duplex              : full
ifindex             : 260
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

_uuid               : 28a24ee7-429b-4c4e-99cc-a970313ca1fd
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2035185950, tx_dropped=0, tx_errors=0, tx_packets=104476111}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 63502553-693e-4479-8476-1562bcad4131
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2886674908, tx_dropped=0, tx_errors=0, tx_packets=7651073}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6cac056e1d3773ec38e5667da8fc677024248712
Author:     Ankur Sharma &lt;ankursharma@vmware.com&gt;
AuthorDate: Fri Oct 17 11:12:32 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Oct 17 13:59:09 2014 -0700

    datapath-windows: netdev-windows fixes for vswitchd bringup.
    
    Added the handlers for update_flags and set_etheraddr.
    These handlers were needed for vswitchd bringup on windows
    platform.
    
    Signed-off-by: Ankur Sharma &lt;ankursharma@vmware.com&gt;
    Acked-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
