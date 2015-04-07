---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
5753a3e7-1950-4cf3-9e62-b6f416bd95bb
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b366438e-fe84-4edf-84c7-fac0dd6a8eec
controller          : [6b8e9f0c-056d-4bc0-bf02-cdbb04cf5467]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [84213a6e-8feb-4a00-9642-dc6d76bdf156, 903049c1-6244-4cf8-8a38-afa23dbb203d, ce729f9a-4f77-48e0-9972-681e5f7bb10d, ceba50bb-0786-44d9-a9f0-482c2b0de68e]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6b8e9f0c-056d-4bc0-bf02-cdbb04cf5467
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="657", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 903049c1-6244-4cf8-8a38-afa23dbb203d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c878f276-b504-461e-894f-bd86c4e34a88]
name                : "eth22"

_uuid               : ce729f9a-4f77-48e0-9972-681e5f7bb10d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [60807fb0-9854-4ac6-afd7-c31932583e9a]
name                : "eth23"

_uuid               : 84213a6e-8feb-4a00-9642-dc6d76bdf156
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [85f702f1-817d-4761-9484-f1d8c706ebf6]
name                : "eth21"

_uuid               : ceba50bb-0786-44d9-a9f0-482c2b0de68e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [885f99a0-62a9-4769-a89d-876b1d4413e2]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 885f99a0-62a9-4769-a89d-876b1d4413e2
admin_state         : down
duplex              : full
ifindex             : 871
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

_uuid               : 60807fb0-9854-4ac6-afd7-c31932583e9a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=39833235000, tx_dropped=0, tx_errors=0, tx_packets=26555490}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 85f702f1-817d-4761-9484-f1d8c706ebf6
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
statistics          : {collisions=0, rx_bytes=1218847669790, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=812928310, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c878f276-b504-461e-894f-bd86c4e34a88
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=619954336658, tx_dropped=0, tx_errors=0, tx_packets=413462634}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f293a803d9ece7157ec5d098deb1bf29e5de5915
Author:     Kevin Lo &lt;kevlo@FreeBSD.org&gt;
AuthorDate: Tue Apr 7 16:18:47 2015 +0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Apr 7 05:57:52 2015 -0700

    specify -w to set variables for sysctl&#40;8&#41; on NetBSD
    
    We have to specify -w to set tunable sysctls on NetBSD.
    
    Signed-off-by: Kevin Lo &lt;kevlo at FreeBSD.org&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
</pre>
