---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2713a6bc-cfba-40bd-820d-3e6b27e91cd0
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
_uuid               : 80ba7021-e93a-4a44-83b1-786a37fa74cd
controller          : [eae3f711-d09c-41e4-bee8-6f0b9bfe05db]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3f043868-5b6c-4450-b9eb-11ea59700de1, 41460f9a-2572-428d-a2c0-c7ab1d296d99, 8fccf453-b127-431d-a989-a1e52be4e55a, d9dad53b-0a13-4e6c-8920-6d581ce8af82]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : eae3f711-d09c-41e4-bee8-6f0b9bfe05db
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="767", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3f043868-5b6c-4450-b9eb-11ea59700de1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8c03759e-8c9a-4a43-a429-8727b88156f7]
name                : "br0"

_uuid               : 41460f9a-2572-428d-a2c0-c7ab1d296d99
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [306895f6-3a28-42ac-9cb7-f43f625aa42f]
name                : "eth21"

_uuid               : 8fccf453-b127-431d-a989-a1e52be4e55a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fbf67300-98a9-4388-a99c-05c4b0349f13]
name                : "eth22"

_uuid               : d9dad53b-0a13-4e6c-8920-6d581ce8af82
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e8aef187-3bff-4c9e-b053-720479779018]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : fbf67300-98a9-4388-a99c-05c4b0349f13
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28645194742, tx_dropped=0, tx_errors=0, tx_packets=19115170}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 8c03759e-8c9a-4a43-a429-8727b88156f7
admin_state         : down
duplex              : full
ifindex             : 632
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

_uuid               : 306895f6-3a28-42ac-9cb7-f43f625aa42f
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
statistics          : {collisions=0, rx_bytes=40991653660, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27369603, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : e8aef187-3bff-4c9e-b053-720479779018
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5416296000, tx_dropped=0, tx_errors=0, tx_packets=3610864}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 09dc775746897103f76af5477db5096a9dfb4d5b
Author:     Ben Pfaff &lt;blp@ovn.org&gt;
AuthorDate: Fri Nov 6 10:56:14 2015 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Sat Nov 7 17:07:43 2015 -0800

    AUTHORS: Update my email address.
    
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
    Acked-by: Justin Pettit &lt;jpettit@ovn.org&gt;
</pre>
