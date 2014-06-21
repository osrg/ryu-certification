---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
48d9edac-d552-420f-9838-71baa201a984
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 867c8a32-1138-4276-b732-23e3af2cefaf
controller          : [94fa52ea-bdd2-4a3a-b8c1-8149db34e670]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [3d7ddb93-d8aa-4588-9afc-fb3c4167ed37, 5e68022f-9470-4f40-b87d-2662f44ee955, 6470e8cc-5047-4aad-b040-3ff0335d8fb9, c10e4e7d-9d31-4a6a-b605-44f5f1471f8d]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 94fa52ea-bdd2-4a3a-b8c1-8149db34e670
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=977, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6470e8cc-5047-4aad-b040-3ff0335d8fb9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2c304b71-252c-4d20-b3e6-0d911dc05ef1]
name                : eth22

_uuid               : c10e4e7d-9d31-4a6a-b605-44f5f1471f8d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [431fa25a-2671-4c13-853b-36b547b6524d]
name                : br0

_uuid               : 3d7ddb93-d8aa-4588-9afc-fb3c4167ed37
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cb258b45-c949-4d38-b2ed-433c95c27182]
name                : eth23

_uuid               : 5e68022f-9470-4f40-b87d-2662f44ee955
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [64a623d7-5ab7-42a5-9e11-9b8315482a76]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : cb258b45-c949-4d38-b2ed-433c95c27182
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=836561080, tx_dropped=0, tx_errors=0, tx_packets=9148326}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2c304b71-252c-4d20-b3e6-0d911dc05ef1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2132316441, tx_dropped=0, tx_errors=0, tx_packets=21502242}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 431fa25a-2671-4c13-853b-36b547b6524d
admin_state         : down
duplex              : full
ifindex             : 557
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

_uuid               : 64a623d7-5ab7-42a5-9e11-9b8315482a76
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
statistics          : {collisions=0, rx_bytes=437307315, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=43337481, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 2791461076c73d063b60ed1a3a56baeab38d354b
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Fri Jun 20 17:41:45 2014 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Fri Jun 20 17:41:45 2014 -0700

    datapath: Check tunnel info before dereferencing on send.
    
    It's possible that the tunnel information may not have been set by
    userspace before a packet is output to a tunnel port. Therefore, we
    should ensure that we validate that the information is there before
    attempting to use it.
    
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
