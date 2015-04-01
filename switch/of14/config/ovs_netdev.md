---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
adecc102-27de-4eb1-aad2-1f47fb8004a6
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
_uuid               : 35e1bf2c-a7c9-4482-b4c7-078381eb6928
controller          : [642a2ec9-e890-48fb-a08b-3a5d1e228e4a]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [91aba162-96e2-44ab-adf6-2f46736d1a6b, d7612650-1321-44ff-8377-d1d33f0283c2, df6cea1e-bec7-4511-99a0-60d3ebbdf206, e9a5df50-f34e-4241-880d-10912aaf310e]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 642a2ec9-e890-48fb-a08b-3a5d1e228e4a
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="652", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d7612650-1321-44ff-8377-d1d33f0283c2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6c2cd701-24d0-49aa-b956-5bd920d31bf3]
name                : "eth23"

_uuid               : e9a5df50-f34e-4241-880d-10912aaf310e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [62668670-10ff-4be5-9903-e4c7f0f3b348]
name                : "eth22"

_uuid               : df6cea1e-bec7-4511-99a0-60d3ebbdf206
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [96af71ca-7b77-4ffe-a70f-93bdd84c5f99]
name                : "eth21"

_uuid               : 91aba162-96e2-44ab-adf6-2f46736d1a6b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1e79401f-7dfd-461d-bd8b-fe52870aba76]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 62668670-10ff-4be5-9903-e4c7f0f3b348
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=611139500797, tx_dropped=0, tx_errors=0, tx_packets=407580791}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 6c2cd701-24d0-49aa-b956-5bd920d31bf3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=38497023000, tx_dropped=0, tx_errors=0, tx_packets=25664682}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 96af71ca-7b77-4ffe-a70f-93bdd84c5f99
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
statistics          : {collisions=0, rx_bytes=1205548340811, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=804051210, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1e79401f-7dfd-461d-bd8b-fe52870aba76
admin_state         : down
duplex              : full
ifindex             : 839
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
commit 508624b691e1517e4d426aa69165ea1efba80d53
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Mar 19 21:00:46 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Mar 31 17:11:21 2015 -0700

    ovsdb-server: Correct malformed error replies to certain JSON-RPC requests.
    
    I realized that this bug existed only a few weeks ago, but it has been
    there since the earliest ovsdb-server code.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
