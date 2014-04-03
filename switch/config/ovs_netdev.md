---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
42073dce-a26c-4431-bfc9-822a228fb6e6
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 5f1948a1-f092-483a-9426-794eeea6b9f2
controller          : [7ed0e519-6aef-483c-b9c9-621577148ad7]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2a456c5c-4750-4df3-b0cf-a9901aa2ad33, 76c620ca-59ab-409e-bfd7-600bb0ad9b22, b7d69569-d01d-4638-87c8-ebf8ec782ad7]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7ed0e519-6aef-483c-b9c9-621577148ad7
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=301, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2a456c5c-4750-4df3-b0cf-a9901aa2ad33
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b2383c9a-9a62-48af-bbb2-f62bd20fbc46]
name                : eth8

_uuid               : b7d69569-d01d-4638-87c8-ebf8ec782ad7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [62ade2b3-3935-4f38-8c74-027239c149f8]
name                : eth7

_uuid               : 76c620ca-59ab-409e-bfd7-600bb0ad9b22
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dab1d0a1-6ef2-49bb-8a2d-ff0c62a67e39]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : dab1d0a1-6ef2-49bb-8a2d-ff0c62a67e39
admin_state         : up
duplex              : full
ifindex             : 857
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : b2383c9a-9a62-48af-bbb2-f62bd20fbc46
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6576269, tx_dropped=0, tx_errors=0, tx_packets=70099}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 62ade2b3-3935-4f38-8c74-027239c149f8
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
statistics          : {collisions=0, rx_bytes=3072957602, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72733615, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 48f6e410db6b2cb036b5fdcde89017101c83590c
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed Apr 2 08:43:17 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Apr 3 07:54:04 2014 -0700

    jsonrpc-server: Combine notifications when connection becomes backlogged.
    
    Connections that queue up too much data, because they are monitoring a
    table that is changing quickly and failing to keep up with the updates,
    cause problems with buffer management.  Since commit 60533a405b2e
    (jsonrpc-server: Disconnect connections that queue too much data.),
    ovsdb-server has dealt with them by disconnecting the connection and
    letting them start up again with a fresh copy of the database.  However,
    this is not ideal because of situations where disconnection happens
    repeatedly.  For example:
    
         - A manager toggles a column back and forth between two or more values
           quickly (in which case the data transmitted over the monitoring
           connections always increases quickly, without bound).
    
         - A manager repeatedly extends the contents of some column in some row
           (in which case the data transmitted over the monitoring connection
           grows with O(n**2) in the length of the string).
    
    A better way to deal with this problem is to combine updates when they are
    sent to the monitoring connection, if that connection is not keeping up.
    In both the above cases, this reduces the data that must be sent to a
    manageable amount.  This commit implements this new way.
    
    Bug #1211786.
    Bug #1221378.
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
