---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
18d3d33e-6340-45d2-9e9a-51d1c00a5b74
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ac8425fb-49da-43a8-adeb-2559394cf465
controller          : [853e6b0a-8639-40b6-8f1e-868cf41b1a15]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1a290f8b-a9b6-4049-b6ee-44e505f3303c, 1ab08747-39d6-44aa-bf28-2cecffd63034, 4542a36f-0882-410b-8a0b-203ff921dd37, e2afa301-2063-4fd2-9652-bee63abc361c]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 853e6b0a-8639-40b6-8f1e-868cf41b1a15
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e2afa301-2063-4fd2-9652-bee63abc361c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3e3d4c71-408b-4642-a683-c9acfa17c728]
name                : "eth23"

_uuid               : 4542a36f-0882-410b-8a0b-203ff921dd37
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bc5ea9e6-192a-4edb-a4ea-b30b5b700603]
name                : "br0"

_uuid               : 1ab08747-39d6-44aa-bf28-2cecffd63034
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b3f6dc5f-d540-40d0-89a2-3ee93f6d0225]
name                : "eth22"

_uuid               : 1a290f8b-a9b6-4049-b6ee-44e505f3303c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [39b61288-36fb-42e2-9de2-fd63d3a55731]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 39b61288-36fb-42e2-9de2-fd63d3a55731
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

_uuid               : 3e3d4c71-408b-4642-a683-c9acfa17c728
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

_uuid               : bc5ea9e6-192a-4edb-a4ea-b30b5b700603
admin_state         : down
duplex              : full
ifindex             : 399
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

_uuid               : b3f6dc5f-d540-40d0-89a2-3ee93f6d0225
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit abd0694c5de8201b68dca2b393adf054b0fb1d2c
Author:     Alin Serdean &lt;aserdean@cloudbasesolutions.com&gt;
AuthorDate: Mon Jul 13 16:42:28 2015 +0000
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Aug 28 11:09:12 2015 -0700

    datapath-windows: Suppress flow attribute probe.
    
    This patch surpresses flow attribute probing in the windows datapath.
    
    Signed-off-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Acked-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
