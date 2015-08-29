---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1591977c-c8ed-44da-94f2-b592fc5c17e3
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : cb095b25-32c4-4079-a636-9fffd995309d
controller          : [7fcf578c-721a-4748-a585-32acfa8161a4]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [9b4b6019-7776-4c45-b485-4efa6805e3d7, 9e5b4993-22c5-443f-88f8-4f22d1406b9b, e90aeadb-62bf-4b03-92eb-b2edec571d4f, e947eac2-1663-4d88-8841-18e78ee96f1c]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7fcf578c-721a-4748-a585-32acfa8161a4
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9b4b6019-7776-4c45-b485-4efa6805e3d7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a8c37f40-e6d1-4b89-b49c-c0e1615a7623]
name                : "eth21"

_uuid               : e947eac2-1663-4d88-8841-18e78ee96f1c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5b7e2320-07b6-4bc3-9b90-5e310c42a419]
name                : "br0"

_uuid               : e90aeadb-62bf-4b03-92eb-b2edec571d4f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [128efacc-9a38-40ea-aace-bdf221a85bb2]
name                : "eth22"

_uuid               : 9e5b4993-22c5-443f-88f8-4f22d1406b9b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8c91ee5f-6c12-4d7e-a089-a5d155ba2cf5]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 5b7e2320-07b6-4bc3-9b90-5e310c42a419
admin_state         : down
duplex              : full
ifindex             : 405
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

_uuid               : 128efacc-9a38-40ea-aace-bdf221a85bb2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18089315792, tx_dropped=0, tx_errors=0, tx_packets=12064077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a8c37f40-e6d1-4b89-b49c-c0e1615a7623
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
statistics          : {collisions=0, rx_bytes=24024581534, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16026376, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 8c91ee5f-6c12-4d7e-a089-a5d155ba2cf5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1176922500, tx_dropped=0, tx_errors=0, tx_packets=784615}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 14dd55a3e3496057e7a7e0281a782b180714348d
Author:     Alex Wang &lt;ee07b291@gmail.com&gt;
AuthorDate: Fri Aug 21 15:20:24 2015 -0700
Commit:     Alex Wang &lt;ee07b291@gmail.com&gt;
CommitDate: Sat Aug 29 00:48:21 2015 +0000

    bridge: Relax the whitelist format for punix path.
    
    This commit relaxes the whitelist format for punix path of
    service controller.  Instead of only allowing
    punix:&lt;ovs_rundir&gt;/&lt;bridge_name&gt;.controller, the new format
    allows any suffix, like punix:&lt;ovs_rundir&gt;/&lt;bridge_name&gt;.*.
    &#40;except one containing '/'&#41;.
    
    Signed-off-by: Alex Wang &lt;ee07b291@gmail.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
