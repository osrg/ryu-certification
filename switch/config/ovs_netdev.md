---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a4ac770d-94b3-4482-ac4c-00e439763022
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8c1b212a-4614-4bc6-891c-f09148296cc3
controller          : [0cd5795e-d365-497a-bcbd-5ce1eb199eaf]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [31cdff90-7a49-473f-97ca-db3ec23f5ec8, 3a6cd944-f47a-4388-855d-d28cec641fc7, 851f48f4-8a4a-4832-b2fc-22def04f57a9, 8a1ae99f-f873-4253-8423-54cffdf71123]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0cd5795e-d365-497a-bcbd-5ce1eb199eaf
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=697, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3a6cd944-f47a-4388-855d-d28cec641fc7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [06230f3c-932c-41f8-ae6b-6b686b9d1616]
name                : eth23

_uuid               : 31cdff90-7a49-473f-97ca-db3ec23f5ec8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2001c98e-03b8-43ee-8364-42ae5bff2fb7]
name                : eth22

_uuid               : 851f48f4-8a4a-4832-b2fc-22def04f57a9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cbf3a784-b979-4560-a63b-9828780bc544]
name                : br0

_uuid               : 8a1ae99f-f873-4253-8423-54cffdf71123
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d8ad2016-48b7-4b76-996c-798d5c4a2f1d]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 06230f3c-932c-41f8-ae6b-6b686b9d1616
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=57723612, tx_dropped=0, tx_errors=0, tx_packets=8628417}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : cbf3a784-b979-4560-a63b-9828780bc544
admin_state         : down
duplex              : full
ifindex             : 293
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

_uuid               : 2001c98e-03b8-43ee-8364-42ae5bff2fb7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2939390312, tx_dropped=0, tx_errors=0, tx_packets=105083799}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d8ad2016-48b7-4b76-996c-798d5c4a2f1d
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
statistics          : {collisions=0, rx_bytes=3303056741, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=171237117, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ee4dac3bb6dcef43c51f7ddf3ad954eab4c9ed0f
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Tue Oct 28 10:01:22 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Oct 28 10:46:07 2014 -0700

    netdev-windows: Fix bugs in flag update and MAC address copy functions.
    
    The .update_flags function in netdev-windows was dummy. But we need to
    return the existing flags for link status to be shown as up in the
    confdb.
    
    There was a bug in copying the MAC address.
    
    We fix these two issues in this patch.
    
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Co-Authored-by: Ankur Sharma &lt;ankursharma@vmware.com&gt;
    Signed-off-by: Ankur Sharma &lt;ankursharma@vmware.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Tested-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
