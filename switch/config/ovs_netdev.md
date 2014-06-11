---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a2d99d76-7fce-4408-b950-f4f6b0123b3a
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8e65e0c0-17a3-443d-9d1a-f9ba5cba449a
controller          : [e666fb3e-e614-435e-bb39-b6568bc72bf7]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0c4beadf-fcd1-4c59-be81-76d1f1de3c9b, 69b193bd-5135-454d-a574-37a9eea5540e, c28bdd42-fc3d-45d7-b2df-852c0823cd51, e5809c2d-9f0a-41ab-bb2f-a3612a28b226]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e666fb3e-e614-435e-bb39-b6568bc72bf7
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=967, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 69b193bd-5135-454d-a574-37a9eea5540e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [74f85b7c-8e8c-4809-b8f4-6015144f2bda]
name                : br0

_uuid               : e5809c2d-9f0a-41ab-bb2f-a3612a28b226
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4783b8c7-c376-48b0-a69a-c5b4a52ad468]
name                : eth21

_uuid               : c28bdd42-fc3d-45d7-b2df-852c0823cd51
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [13ead188-0a8b-41e4-8997-3e06fbd21e12]
name                : eth23

_uuid               : 0c4beadf-fcd1-4c59-be81-76d1f1de3c9b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cd0fb1ab-ad99-4450-bd04-1332b0e3c851]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 74f85b7c-8e8c-4809-b8f4-6015144f2bda
admin_state         : down
duplex              : full
ifindex             : 448
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

_uuid               : 13ead188-0a8b-41e4-8997-3e06fbd21e12
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2038133908, tx_dropped=0, tx_errors=0, tx_packets=7085379}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 4783b8c7-c376-48b0-a69a-c5b4a52ad468
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
statistics          : {collisions=0, rx_bytes=1129868298, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26591392, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : cd0fb1ab-ad99-4450-bd04-1332b0e3c851
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1518486926, tx_dropped=0, tx_errors=0, tx_packets=12490500}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5349904d1b80152a9299022b6d529154736f20ce
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Fri May 23 13:26:18 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Wed Jun 11 13:53:29 2014 -0700

    socket-util: Disable dscp setting on Windows.
    
    According to msdn documentation, one is discouraged from using
    IP_TOS for ipv4 sockets &#40;it apparently does not actually set
    anything&#41;. Also, IPV6_TCLASS does not work in
    Windows &#40;it always returns an error and also is undocumented&#41;.
    Looks like Microsoft recommends QoS2 APIs to achieve
    the same. Till we add those API calls, simply return on Windows.
    
    &#40;Noticed while running unit tests for ipv6. set_dscp would fail.&#41;
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
