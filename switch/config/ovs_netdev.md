---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8e1dda0f-6870-41d5-bded-d4c1ee919334
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth8"
            Interface "eth8"
        Port "eth7"
            Interface "eth7"

$ sudo ovs-vsctl list Bridge
_uuid               : 0118b94d-959b-4769-a458-679f63b0ecf2
controller          : [f0aa3313-4bf7-4d1d-832b-68d804a3c08d]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [218e9e5c-cbfc-4a21-b4b3-fc1252bf5af4, 8eaaba7d-f6b9-4260-91db-dd5481409fa7, f17933f4-be06-453d-bc0f-af36547c335f]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : f0aa3313-4bf7-4d1d-832b-68d804a3c08d
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="322", sec_since_disconnect="4", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 218e9e5c-cbfc-4a21-b4b3-fc1252bf5af4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ff4bf7c8-1063-4021-b2d0-c983a18106db]
name                : "br0"

_uuid               : f17933f4-be06-453d-bc0f-af36547c335f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aa2b752d-af85-4504-a16a-ac03ddc35a7f]
name                : "eth7"

_uuid               : 8eaaba7d-f6b9-4260-91db-dd5481409fa7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d2032825-efdd-4b25-85af-a43d87ddd7a3]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : ff4bf7c8-1063-4021-b2d0-c983a18106db
admin_state         : up
duplex              : full
ifindex             : 107
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : d2032825-efdd-4b25-85af-a43d87ddd7a3
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:ec"
mtu                 : 1550
name                : "eth8"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=768856, tx_dropped=0, tx_errors=0, tx_packets=8294}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : aa2b752d-af85-4504-a16a-ac03ddc35a7f
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "eth7"
ofport              : 1
statistics          : {collisions=0, rx_bytes=2268596, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=23062, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 89e45da9c16fd9dbed78feb74b1a55b332ba95a7
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Wed Jan 8 15:07:30 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Jan 7 22:18:08 2014 -0800

    Fix !HAVE_NETLINK build
    
    Fix a regression introduced by commit 4b97b70d
    ("ofproto-dpif: Enable NXAST_SAMPLE only if the datapath supports it.")
    
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
