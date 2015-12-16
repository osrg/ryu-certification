---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
14d43ab1-99db-4c48-9bf9-3698a959dac8
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c2337917-15b0-4ade-aaf8-6b1367675276
controller          : [88bd165c-dfc8-4ee5-9fcf-175ad13879d4]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [4a92e325-8ac0-4169-91a0-365a7f44c63e, 624f82fe-4b9f-46df-8cca-062613997013, 7121a939-a091-4cc2-9d2d-0c24952099ab, 8dc3a814-d967-478c-ad0b-4b17d28a9812]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 88bd165c-dfc8-4ee5-9fcf-175ad13879d4
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="4", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8dc3a814-d967-478c-ad0b-4b17d28a9812
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [baf0947e-9a02-4e3a-ac2d-f7aad948a104]
name                : "eth22"

_uuid               : 7121a939-a091-4cc2-9d2d-0c24952099ab
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d0658541-3f4b-42ef-80a4-a7f50408a375]
name                : "eth21"

_uuid               : 4a92e325-8ac0-4169-91a0-365a7f44c63e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7b5c64d2-3044-42c1-9032-24ed3f8b4a39]
name                : "br0"

_uuid               : 624f82fe-4b9f-46df-8cca-062613997013
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [655b8296-6cf7-410a-add6-8309664eca88]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d0658541-3f4b-42ef-80a4-a7f50408a375
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=42629969634, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28471022, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 655b8296-6cf7-410a-add6-8309664eca88
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6644245500, tx_dropped=0, tx_errors=0, tx_packets=4429497}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : baf0947e-9a02-4e3a-ac2d-f7aad948a104
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29382603104, tx_dropped=0, tx_errors=0, tx_packets=19611266}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7b5c64d2-3044-42c1-9032-24ed3f8b4a39
admin_state         : down
duplex              : full
ifindex             : 688
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9b5422a98f817b9f2a1f8224cab7e1a8d0bbba1f
Author:     Ilya Maximets &lt;i.maximets@samsung.com&gt;
AuthorDate: Wed Dec 16 15:32:21 2015 +0300
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Wed Dec 16 04:38:11 2015 -0800

    ovs-lib: Try to call exit before killing.
    
    While killing OVS may not free all allocated resources.
    
    Example:
    	Socket for vhost-user port will stay in a system
    	after 'systemctl stop openvswitch' and opening
    	that port after restart will fail.
    
    Signed-off-by: Ilya Maximets &lt;i.maximets@samsung.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
