---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b227e4ed-ca5c-46d3-ad12-838a62764abd
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : eadb11c2-3be5-428a-9b44-7866b5dd3641
controller          : [92ae39e4-1c0a-44de-a4dd-c809f0c37b92]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [40270df7-c29f-463d-8aca-329f355b058e, 8e45391a-df39-4a44-b0ec-0e7f8886951b, b50af970-a88a-43fe-96f3-bc5a31904061, f1c78abd-71a8-43f4-a35a-3c5dc049bedf]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 92ae39e4-1c0a-44de-a4dd-c809f0c37b92
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=647, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b50af970-a88a-43fe-96f3-bc5a31904061
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [eba57f84-bd55-4355-9f57-37829a7c83c7]
name                : eth23

_uuid               : f1c78abd-71a8-43f4-a35a-3c5dc049bedf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6d2fc6eb-08fa-4fc8-a074-31054e552817]
name                : eth21

_uuid               : 8e45391a-df39-4a44-b0ec-0e7f8886951b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ae1081d4-a70a-4720-9a46-298348cdc08a]
name                : eth22

_uuid               : 40270df7-c29f-463d-8aca-329f355b058e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9c0969aa-10b9-43be-aabc-47f03a8bed7f]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : eba57f84-bd55-4355-9f57-37829a7c83c7
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=3354689784, tx_dropped=0, tx_errors=0, tx_packets=13690390}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ae1081d4-a70a-4720-9a46-298348cdc08a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3012898432, tx_dropped=0, tx_errors=0, tx_packets=36424442}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9c0969aa-10b9-43be-aabc-47f03a8bed7f
admin_state         : down
duplex              : full
ifindex             : 729
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

_uuid               : 6d2fc6eb-08fa-4fc8-a074-31054e552817
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
statistics          : {collisions=0, rx_bytes=1369069078, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=92683935, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f8003b53247ba837ee21ecef85c923124318fef8
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Wed Jun 25 11:06:18 2014 +0900
Commit:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
CommitDate: Thu Jun 26 12:52:41 2014 +0900

    FAQ: add an entry for MAC learning + VLAN
    
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Flavio Leitner &lt;fbl@redhat.com&gt;
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
</pre>
