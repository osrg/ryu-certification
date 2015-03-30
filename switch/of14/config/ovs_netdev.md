---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7f5ccdcf-6865-4ae0-98a3-f168c9fe0bdf
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 5188658d-2644-4d96-a9ba-f45c42c0702d
controller          : [fee9d132-6c9b-48fb-b070-0fc451658341]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3c2e66ae-d837-4f77-a83a-81e4b024cd8d, 3d3825ef-9db6-40c3-9868-a46c54b7c7e4, 43bfa85d-a3e4-4dc2-a2c9-636acc5f6454, e055f10e-c73d-42f2-98fb-a71100209720]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : fee9d132-6c9b-48fb-b070-0fc451658341
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="652", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 43bfa85d-a3e4-4dc2-a2c9-636acc5f6454
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ad28198d-ee54-4b20-970d-f380ece865ed]
name                : "eth23"

_uuid               : 3c2e66ae-d837-4f77-a83a-81e4b024cd8d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5bb5588a-804f-42b0-8180-fd19f5ff6bed]
name                : "eth22"

_uuid               : e055f10e-c73d-42f2-98fb-a71100209720
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7f1405ef-64f1-4bed-9b4a-1b7df6560d8c]
name                : "br0"

_uuid               : 3d3825ef-9db6-40c3-9868-a46c54b7c7e4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d558ed57-838f-420d-beb5-0a6415a4c1c4]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ad28198d-ee54-4b20-970d-f380ece865ed
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=37893888000, tx_dropped=0, tx_errors=0, tx_packets=25262592}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 5bb5588a-804f-42b0-8180-fd19f5ff6bed
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=610424155193, tx_dropped=0, tx_errors=0, tx_packets=407101384}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7f1405ef-64f1-4bed-9b4a-1b7df6560d8c
admin_state         : down
duplex              : full
ifindex             : 825
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

_uuid               : d558ed57-838f-420d-beb5-0a6415a4c1c4
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
statistics          : {collisions=0, rx_bytes=1204449409083, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=803313501, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7ad20cbd96b9b33a2e01be36dc51674fde8b67bf
Author:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
AuthorDate: Fri Mar 27 16:29:50 2015 +0000
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Mon Mar 30 13:17:41 2015 -0700

    dpif-netdev: Account for and free lost packets.
    
    Packets for which an upcall has failed &#40;lost packets&#41; must be deleted.
    We also need to count them as MISS and LOST.
    
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
