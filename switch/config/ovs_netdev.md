---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
84a070b6-488c-4c32-82d6-47db2e3e1d70
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
_uuid               : 83c86a1d-dd13-4d02-9add-0f36182c9538
controller          : [daac7d9f-5616-4fc9-b4eb-1c24b8f15860]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [06ddc25c-df6d-4e70-8585-fa64a8f07209, 632dba8a-789e-4103-ba4f-4633ef81b983, ac6d3caf-5a42-42cf-9c70-dd75cfaaab18, e862cfef-a927-4592-9c7f-516f73c4564c]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : daac7d9f-5616-4fc9-b4eb-1c24b8f15860
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=702, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 06ddc25c-df6d-4e70-8585-fa64a8f07209
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [43218414-6a3a-4f15-8e6d-3f17c1c94a8e]
name                : eth22

_uuid               : 632dba8a-789e-4103-ba4f-4633ef81b983
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e4cce883-53ea-43bf-a2ee-a5ad7d026a0f]
name                : eth23

_uuid               : ac6d3caf-5a42-42cf-9c70-dd75cfaaab18
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [46d605f1-b3c2-4ac3-ac2e-c6530fec1bdd]
name                : br0

_uuid               : e862cfef-a927-4592-9c7f-516f73c4564c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b9a62a0a-7299-470e-86da-222dd1365f13]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 43218414-6a3a-4f15-8e6d-3f17c1c94a8e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=995005984, tx_dropped=0, tx_errors=0, tx_packets=23579334}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 46d605f1-b3c2-4ac3-ac2e-c6530fec1bdd
admin_state         : down
duplex              : full
ifindex             : 83
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

_uuid               : b9a62a0a-7299-470e-86da-222dd1365f13
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
statistics          : {collisions=0, rx_bytes=2286954400, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=33042201, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e4cce883-53ea-43bf-a2ee-a5ad7d026a0f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2930536500, tx_dropped=0, tx_errors=0, tx_packets=1953691}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d6d2a5b381519ad1b52bb3fdd55b59684dbbc1de
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Sep 2 08:35:02 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Sep 2 09:05:45 2014 -0700

    ovs-vsctl: Correctly exit on errors for non-map types in &quot;remove&quot; command.
    
    Reported-by: Thomas Graf &lt;tgraf@noironetworks.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Thomas Graf &lt;tgraf@noironetworks.com&gt;
</pre>
