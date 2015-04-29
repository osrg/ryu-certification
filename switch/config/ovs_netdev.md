---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
302cf405-779d-4712-a684-5d8fbfb3fb70
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
_uuid               : 5a68feac-2a95-4862-a2a5-38d93fe05408
controller          : [80b25875-f432-4885-b049-adf54e3b9663]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [124ec8d9-333e-4892-8be2-e1d62f1a918f, 6b413d06-224b-4280-9038-2aee2bd6e51e, a20d5041-83d5-4cd5-9d45-fd9f69f2790b, d08ac74d-86f8-447e-9143-49a4a56bb65f]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 80b25875-f432-4885-b049-adf54e3b9663
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="656", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 124ec8d9-333e-4892-8be2-e1d62f1a918f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ba20889d-acce-44a8-a8c8-229738774e99]
name                : "br0"

_uuid               : d08ac74d-86f8-447e-9143-49a4a56bb65f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9061f7a3-b3dc-4dc0-a12d-ead99f82a926]
name                : "eth23"

_uuid               : a20d5041-83d5-4cd5-9d45-fd9f69f2790b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cd38f154-a797-4eea-9cef-b3293ff1c6ac]
name                : "eth22"

_uuid               : 6b413d06-224b-4280-9038-2aee2bd6e51e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [34a96210-de53-48e2-8a36-703de560ced4]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 34a96210-de53-48e2-8a36-703de560ced4
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
statistics          : {collisions=0, rx_bytes=1235115849586, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=823802149, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : cd38f154-a797-4eea-9cef-b3293ff1c6ac
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=631731113608, tx_dropped=0, tx_errors=0, tx_packets=421327045}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ba20889d-acce-44a8-a8c8-229738774e99
admin_state         : down
duplex              : full
ifindex             : 955
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

_uuid               : 9061f7a3-b3dc-4dc0-a12d-ead99f82a926
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=43563255000, tx_dropped=0, tx_errors=0, tx_packets=29042170}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 4237026e52f6bfa1dac0162dd82f7bb3f26c833d
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Thu Apr 9 20:12:32 2015 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Wed Apr 29 10:33:18 2015 -0700

    datapath: Add Stateless TCP Tunneling protocol.
    
    The Stateless TCP Tunnel &#40;STT&#41; protocol encapsulates traffic in
    IPv4/TCP packets.
    STT uses TCP segmentation offload available in most of NIC. On
    packet xmit STT driver appends STT header along with TCP header
    to the packet. For GSO packet GSO parameters are set according
    to tunnel configuration and packet is handed over to networking
    stack. This allows use of segmentation offload available in NICs
    
    The protocol is documented at
    http://www.ietf.org/archive/id/draft-davie-stt-06.txt
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
