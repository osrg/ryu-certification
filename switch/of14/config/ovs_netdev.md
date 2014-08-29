---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f193c8b1-bd76-4d4f-a3f8-0c06c268bc5c
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c0ca7858-a228-4e89-ba97-e73b0cfbff7a
controller          : [7d5bb91b-fed3-4ab7-a9cb-25be10f929b2]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [54f0cdf8-7d68-4fbc-ad36-3fdeb71a3221, 57fb0cc8-4477-4bf1-b018-6e298b6bd20a, 69256f7e-f15f-4915-ab1e-de22069ce531, 7d6a5f5e-49c0-443a-af97-118bea389ccd]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7d5bb91b-fed3-4ab7-a9cb-25be10f929b2
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=672, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 57fb0cc8-4477-4bf1-b018-6e298b6bd20a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [46363f74-e887-4d8b-b972-18cc7916a633]
name                : eth21

_uuid               : 54f0cdf8-7d68-4fbc-ad36-3fdeb71a3221
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9860691e-08ca-42d6-9d0e-dabeec19ea31]
name                : br0

_uuid               : 7d6a5f5e-49c0-443a-af97-118bea389ccd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [27bc0cb7-1e85-405f-a6fd-4137d2217be7]
name                : eth23

_uuid               : 69256f7e-f15f-4915-ab1e-de22069ce531
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a12b1b7a-8ec7-476e-b633-db103badedf8]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 46363f74-e887-4d8b-b972-18cc7916a633
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
statistics          : {collisions=0, rx_bytes=857130360, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=17768890, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a12b1b7a-8ec7-476e-b633-db103badedf8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2424617996, tx_dropped=0, tx_errors=0, tx_packets=13077670}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9860691e-08ca-42d6-9d0e-dabeec19ea31
admin_state         : down
duplex              : full
ifindex             : 75
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

_uuid               : 27bc0cb7-1e85-405f-a6fd-4137d2217be7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2512507500, tx_dropped=0, tx_errors=0, tx_packets=1675005}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a139efa9e4c1250787be2c28fc2a06c9ff1f91f6
Author:     Thomas Graf &lt;tgraf@noironetworks.com&gt;
AuthorDate: Fri Aug 29 19:56:26 2014 +0200
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Aug 29 13:53:11 2014 -0700

    travis: Add build@openvswitch.org email list for build notifications.
    
    Enable build notifications to build@openvswitch.org
    
    Co-authored-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Thomas Graf &lt;tgraf@noironetworks.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
