---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
52122a3d-639e-4bca-a3fd-2979e967244b
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b4653ff7-a975-47c4-95c2-452fa4c8c005
controller          : [11def6d7-60e2-46a3-bf37-6e8c0ec8fe01]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [74ca93d8-4ee8-409f-93a9-c3a3fb60f5ec, 7d1a6b1c-e1e2-42b4-b220-79e20c1e0264, f08d3283-c69f-417b-bc26-2e5ce64cdc77, f67e6d12-142b-45bb-8c42-792ae92e019b]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 11def6d7-60e2-46a3-bf37-6e8c0ec8fe01
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="16", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 74ca93d8-4ee8-409f-93a9-c3a3fb60f5ec
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2d957c1a-0461-428c-8dac-123a345aae8a]
name                : "eth23"

_uuid               : 7d1a6b1c-e1e2-42b4-b220-79e20c1e0264
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ddbecaa3-8771-4e02-92cc-5de2e9341093]
name                : "eth22"

_uuid               : f67e6d12-142b-45bb-8c42-792ae92e019b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ac584c55-562d-40b1-b44d-9295814e7653]
name                : "eth21"

_uuid               : f08d3283-c69f-417b-bc26-2e5ce64cdc77
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bce625d7-c5ac-42e9-abcf-4e7720cda937]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ac584c55-562d-40b1-b44d-9295814e7653
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
statistics          : {collisions=0, rx_bytes=46140513348, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30831111, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 2d957c1a-0461-428c-8dac-123a345aae8a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9275847000, tx_dropped=0, tx_errors=0, tx_packets=6183898}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : bce625d7-c5ac-42e9-abcf-4e7720cda937
admin_state         : down
duplex              : full
ifindex             : 804
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

_uuid               : ddbecaa3-8771-4e02-92cc-5de2e9341093
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30962303078, tx_dropped=0, tx_errors=0, tx_packets=20674016}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 598ff4b2d09d8194a40b850b6eb110797ab4d1b2
Author:     Ben Pfaff &lt;blp@ovn.org&gt;
AuthorDate: Tue Feb 16 15:33:42 2016 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Tue Feb 16 21:11:13 2016 -0800

    openflow-common: Describe length and padding rules for OpenFlow properties.
    
    I keep having to rediscover these from the code.  This is easier.
    
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
    Acked-by: Joe Stringer &lt;joe@ovn.org&gt;
</pre>
