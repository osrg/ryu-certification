---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
841c0289-79e7-483c-a240-6290607a7a49
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 915f7af7-b42c-4cb2-bda3-a7839aa97d12
controller          : [fbdeb51a-7bec-40a5-b09c-6a57aad8dda0]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [31bb8cc0-1f3f-4e3a-a353-482a48ddd5fb, 55dfe427-d3c9-45f9-a390-48597ab944f6, 99056072-4dde-4502-aadd-91f08dd730dd, ecbbbec2-f86a-48c2-a935-86b1761f876d]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : fbdeb51a-7bec-40a5-b09c-6a57aad8dda0
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=667, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 31bb8cc0-1f3f-4e3a-a353-482a48ddd5fb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4c642ec6-d74b-4557-a41a-08646e36f937]
name                : eth22

_uuid               : 99056072-4dde-4502-aadd-91f08dd730dd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9c161c4f-9f73-489e-9131-3b4ca482ede5]
name                : eth23

_uuid               : ecbbbec2-f86a-48c2-a935-86b1761f876d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [13d173ef-06e3-4318-87fe-f903322def19]
name                : eth21

_uuid               : 55dfe427-d3c9-45f9-a390-48597ab944f6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [12b291ef-9873-417a-a05e-f8de80e79d0b]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4c642ec6-d74b-4557-a41a-08646e36f937
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1122884280, tx_dropped=0, tx_errors=0, tx_packets=751547}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 12b291ef-9873-417a-a05e-f8de80e79d0b
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

_uuid               : 13d173ef-06e3-4318-87fe-f903322def19
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
statistics          : {collisions=0, rx_bytes=2365711527, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1583687, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9c161c4f-9f73-489e-9131-3b4ca482ede5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=944991000, tx_dropped=0, tx_errors=0, tx_packets=629994}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1a12c419bdbc4a2d458eb8fa07118b4bfc9e0a4f
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed Aug 20 22:22:58 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Aug 21 09:08:03 2014 -0700

    ovs-ofctl: Document that &quot;move&quot; uses a standard action in OF1.5+.
    
    Reported-by: Jean Tourrilhes &lt;jt@hpl.hp.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Jean Tourrilhes &lt;jt@hpl.hp.com&gt;
</pre>
