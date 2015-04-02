---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3730c417-a4e4-4e01-83e2-470f619e68f2
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e5dcfa85-00d2-4eaa-971c-2cf0abb91c41
controller          : [3104b173-6098-4d77-b63a-2c9cc2e70c73]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [6c6bae8a-844b-42e3-b890-9b6a404befb6, 897a4738-b8dd-4172-aefb-5087dea33988, 9aeacff6-dc41-4ea1-a47c-fa6ec85a07d3, b52ee19c-a7c6-4045-a7c1-db5feb191a29]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3104b173-6098-4d77-b63a-2c9cc2e70c73
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="657", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b52ee19c-a7c6-4045-a7c1-db5feb191a29
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fbefdddb-8b13-40b7-878c-c75e13365f88]
name                : "br0"

_uuid               : 897a4738-b8dd-4172-aefb-5087dea33988
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [02023e34-338a-4989-bfb7-d7415087ad2d]
name                : "eth22"

_uuid               : 9aeacff6-dc41-4ea1-a47c-fa6ec85a07d3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5fb30831-6398-4384-a635-f989d4930c2e]
name                : "eth23"

_uuid               : 6c6bae8a-844b-42e3-b890-9b6a404befb6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [51fb24a0-6072-4ac5-b3ae-9ed358729aee]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 51fb24a0-6072-4ac5-b3ae-9ed358729aee
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
statistics          : {collisions=0, rx_bytes=1205980827600, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=804341436, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 02023e34-338a-4989-bfb7-d7415087ad2d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=611444764572, tx_dropped=0, tx_errors=0, tx_packets=407785251}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 5fb30831-6398-4384-a635-f989d4930c2e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=38710650000, tx_dropped=0, tx_errors=0, tx_packets=25807100}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : fbefdddb-8b13-40b7-878c-c75e13365f88
admin_state         : down
duplex              : full
ifindex             : 844
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
commit b3cceba0b7c4013f46b01f8987e8716d7857c6db
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Wed Apr 1 16:11:19 2015 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Wed Apr 1 17:02:39 2015 -0700

    bridge: Execute bridge_run&#40;&#41; only after retrieving db contents.
    
    During upgrade of ovs-vswitchd, we do not want to recreate the already
    configured kernel interfaces.  Especially when IP address is assigned to
    the internal port, the recreation will cause the lost of connection.
    Therefore, ovs-vswitchd should read current ovsdb content first and then
    reuse the existing kernel interfaces that are configured in ovsdb.  In
    terms of the code language, ovs-vswitchd should only execute bridge_run&#40;&#41;
    after it finishes reading the ovsdb content.
    
    However, this expected behavior is broken by the recent commit d18e52e
    &#40;ovsdb-idl: Tolerate missing tables and columns.&#41; which causes the
    execution of bridge_run&#40;&#41; before getting the hint of configured interfaces
    from ovsdb.
    
    To fix the issue, this commit makes sure that the execution of bridge_run&#40;&#41;
    happens only after retrieving the ovsdb contents.
    
    VMware-BZ: #1424342
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
