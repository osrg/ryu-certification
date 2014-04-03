---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
33f2f1e8-94b6-4a0d-b03e-b850d0bb8a01
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7059c6d7-7e6a-4147-aff0-678f6e05e75b
controller          : [27b7a575-060e-4590-bcfd-6a30d08f6503]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [106efad1-8506-4987-ab64-ceb5c8dc5ab8, 4d62c508-1079-4a7e-88f5-8cb964c14741, 6764edbd-5b67-454f-9510-368a6cfb5dd6]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 27b7a575-060e-4590-bcfd-6a30d08f6503
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=922, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4d62c508-1079-4a7e-88f5-8cb964c14741
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7d3c037e-cba0-4b70-b97e-ef0b106bd3ce]
name                : br0

_uuid               : 6764edbd-5b67-454f-9510-368a6cfb5dd6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [513a20bd-d8aa-4e98-98bf-1ed68e1aa3b2]
name                : eth8

_uuid               : 106efad1-8506-4987-ab64-ceb5c8dc5ab8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0b125f5e-6cde-46df-ade3-b93d853d6983]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 513a20bd-d8aa-4e98-98bf-1ed68e1aa3b2
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6648885, tx_dropped=0, tx_errors=0, tx_packets=70874}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 0b125f5e-6cde-46df-ade3-b93d853d6983
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=3073206692, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72736154, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 7d3c037e-cba0-4b70-b97e-ef0b106bd3ce
admin_state         : down
duplex              : full
ifindex             : 871
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:4a:84:eb
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
commit 79bda8258b5365438a70d08c74fab903f1dc0a29
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Apr 3 15:27:18 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Apr 3 16:11:09 2014 -0700

    jsonrpc: Return received JSON-RPC messages immediately in jsonrpc_recv().
    
    Until now, jsonrpc_recv() used separate iterations of its loop to receive
    data, feed it to the JSON-RPC parser, and return the received message.
    This is unnecessarily complicated and can occasionally mean that the
    jsonrpc object has received and parsed but not returned a message.  This
    commit refactors the code to receive data, feed it to the parse, and
    return the received message in a single iteration, and simplifies the code
    in the process.
    
    Reported-by: Chris Hydon &lt;chydon@aristanetworks.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
