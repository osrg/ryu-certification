---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c606e28b-ac3b-4c81-a044-73d276fd1390
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 27278ac0-c5b0-4f67-84bd-1f65f19c46d9
controller          : [20d00ffd-7bae-4af4-b14c-a5f8427d50dd]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [154088f7-855b-4342-a25c-262af3473364, 49892e37-3d86-4fba-bad4-81ee242485db, 49d12143-e958-4545-bf99-bbd5fc9d52ed, b3877ca9-3fd2-4c6e-8af9-c767c1e175ff]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 20d00ffd-7bae-4af4-b14c-a5f8427d50dd
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="757", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b3877ca9-3fd2-4c6e-8af9-c767c1e175ff
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9cf43e3b-624a-47bc-8041-bcae57816858]
name                : "eth23"

_uuid               : 154088f7-855b-4342-a25c-262af3473364
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a95846bb-20fe-45bb-b88d-4977658385d5]
name                : "br0"

_uuid               : 49892e37-3d86-4fba-bad4-81ee242485db
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d6637abd-e583-46bf-a16a-adb074c63b75]
name                : "eth21"

_uuid               : 49d12143-e958-4545-bf99-bbd5fc9d52ed
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5d842caf-4c9b-43d3-953b-2a8883888011]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d6637abd-e583-46bf-a16a-adb074c63b75
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
statistics          : {collisions=0, rx_bytes=39131114217, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26119152, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 5d842caf-4c9b-43d3-953b-2a8883888011
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=27770592934, tx_dropped=0, tx_errors=0, tx_packets=18527736}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9cf43e3b-624a-47bc-8041-bcae57816858
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4058958000, tx_dropped=0, tx_errors=0, tx_packets=2705972}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a95846bb-20fe-45bb-b88d-4977658385d5
admin_state         : down
duplex              : full
ifindex             : 589
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
commit 6bb4a18e6c34180f42d3f55b91ac884e1b1a2da9
Author:     Justin Pettit &lt;jpettit@nicira.com&gt;
AuthorDate: Mon Oct 19 15:41:34 2015 -0700
Commit:     Justin Pettit &lt;jpettit@nicira.com&gt;
CommitDate: Mon Oct 19 16:43:53 2015 -0700

    ovn: Reduce range of ACL priorities.
    
    To implement stateful ACLs, we've needed to reserve multiple logical
    flow priorities in the ACL table.  Rather than continue to have a
    strange range of ACL priorities, we'll make ACL priority range 0 to
    32767 and then offset them by 1000 when inserting them into the logical
    flow table.
    
    Signed-off-by: Justin Pettit &lt;jpettit@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
