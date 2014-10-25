---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e84e0dbd-09bf-4269-852f-ada9aa6f9f05
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d55e12b6-4e34-4910-9300-29725a3304ee
controller          : [73a627e4-d121-4014-ac7f-e8af48fcfb11]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [349e038b-fd06-49a4-b4bf-75815927bd0a, 51a6868a-dc14-4821-b687-37620607012c, bed29499-ac29-41b2-8f00-a5c13f68b269, eeb8f388-5b88-40fc-aedc-c8d9ac71b119]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 73a627e4-d121-4014-ac7f-e8af48fcfb11
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=681, sec_since_disconnect=6, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : eeb8f388-5b88-40fc-aedc-c8d9ac71b119
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [abe3d9dc-a411-40d8-994e-94897363bc4f]
name                : eth22

_uuid               : bed29499-ac29-41b2-8f00-a5c13f68b269
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8eeecb0b-bae2-4da5-a064-22a4efe2ce24]
name                : br0

_uuid               : 51a6868a-dc14-4821-b687-37620607012c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0b6be319-a798-4d7c-a0f0-17827234637c]
name                : eth23

_uuid               : 349e038b-fd06-49a4-b4bf-75815927bd0a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2d3faef3-913f-4f36-880a-79b02289a3e6]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : abe3d9dc-a411-40d8-994e-94897363bc4f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2728695172, tx_dropped=0, tx_errors=0, tx_packets=104942164}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0b6be319-a798-4d7c-a0f0-17827234637c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4002340408, tx_dropped=0, tx_errors=0, tx_packets=8394850}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2d3faef3-913f-4f36-880a-79b02289a3e6
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
statistics          : {collisions=0, rx_bytes=2835480909, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=170922875, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8eeecb0b-bae2-4da5-a064-22a4efe2ce24
admin_state         : down
duplex              : full
ifindex             : 285
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
commit 8341662d1b57edc90e7bbc020319b282ca7f3ab2
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Fri Oct 24 08:14:52 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Oct 24 16:49:31 2014 -0700

    netlink-socket: Fix a couple of compilation warnings.
    
    Reported-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Tested-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    [blp@nicira.com replaced conventional cast by CONST_CAST]
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
