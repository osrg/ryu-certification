---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
589888cb-74c1-4169-9a93-ab31c387b6bd
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7a1f7df9-dc86-419d-a2b2-d49566b15ddc
controller          : [6e298606-3c11-42de-a03a-e66262797df4]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1bf6a8d7-5cd4-41a2-966a-971a00f14a17, 90299038-4f90-4cfa-81eb-7e1e6d3114d0, aa65fa21-6806-4c13-8f42-0b7457c39e05, e04b218e-4505-4d39-8017-39131d528bd2]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6e298606-3c11-42de-a03a-e66262797df4
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="652", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 90299038-4f90-4cfa-81eb-7e1e6d3114d0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4a6f8153-3a6e-489c-b437-facd4850f607]
name                : "br0"

_uuid               : aa65fa21-6806-4c13-8f42-0b7457c39e05
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3fe3700d-90dd-4f13-b9c4-27ee5ff561d9]
name                : "eth23"

_uuid               : e04b218e-4505-4d39-8017-39131d528bd2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b26501c4-1ff7-466d-b2f8-0be0e05089a7]
name                : "eth21"

_uuid               : 1bf6a8d7-5cd4-41a2-966a-971a00f14a17
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1cf62103-335d-4148-807f-e22a7f309ad4]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b26501c4-1ff7-466d-b2f8-0be0e05089a7
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
statistics          : {collisions=0, rx_bytes=1230790191061, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=820894606, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 3fe3700d-90dd-4f13-b9c4-27ee5ff561d9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=40318930500, tx_dropped=0, tx_errors=0, tx_packets=26879287}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 4a6f8153-3a6e-489c-b437-facd4850f607
admin_state         : down
duplex              : full
ifindex             : 881
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

_uuid               : 1cf62103-335d-4148-807f-e22a7f309ad4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=629785276859, tx_dropped=0, tx_errors=0, tx_packets=420018567}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0be55e389d2f12dbbf5dca5c16a7b2c8177e58ff
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Thu Apr 9 08:54:23 2015 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Thu Apr 9 13:52:10 2015 -0700

    INSTALL.Windows: Add documentation about Windows services.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Nithin Raju &lt;nithin@vmware.com&gt;
</pre>
