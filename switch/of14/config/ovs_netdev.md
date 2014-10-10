---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
57b773fb-e5fb-46d9-a54f-3fca611ae6ac
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 410f37ec-c58f-4095-8247-4aba5c9a66d3
controller          : [d42826d5-4117-41d7-bdc9-f0a3bb1b76ac]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2261b3a7-24b1-4e25-b1e7-c586adf98ce3, 2a03dca5-5ef0-4b0b-b617-95080b9ad818, 3694ac8b-1b1e-4c4f-b838-4a3638656afd, ea5fe947-82ca-4d69-bf76-1423df555f18]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d42826d5-4117-41d7-bdc9-f0a3bb1b76ac
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=672, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2a03dca5-5ef0-4b0b-b617-95080b9ad818
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5797a22f-9d13-4a81-a237-6a0c1050f975]
name                : eth21

_uuid               : ea5fe947-82ca-4d69-bf76-1423df555f18
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bf657266-4e9b-40d7-bcbf-08b962851b0e]
name                : br0

_uuid               : 2261b3a7-24b1-4e25-b1e7-c586adf98ce3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6a9cc0a9-79f3-4fe5-b64d-e8120641b880]
name                : eth23

_uuid               : 3694ac8b-1b1e-4c4f-b838-4a3638656afd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4353cfe5-ef9f-470c-829d-8cabb453868c]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6a9cc0a9-79f3-4fe5-b64d-e8120641b880
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1537874908, tx_dropped=0, tx_errors=0, tx_packets=6751873}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 4353cfe5-ef9f-470c-829d-8cabb453868c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3711653700, tx_dropped=0, tx_errors=0, tx_packets=88409111}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : bf657266-4e9b-40d7-bcbf-08b962851b0e
admin_state         : down
duplex              : full
ifindex             : 232
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

_uuid               : 5797a22f-9d13-4a81-a237-6a0c1050f975
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
statistics          : {collisions=0, rx_bytes=349081297, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=146340292, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit bd7fe4e925d73dff879a4a1ac19a4365365e0dd7
Author:     Dmitry Krivenok &lt;krivenok.dmitry@gmail.com&gt;
AuthorDate: Fri Oct 10 08:56:22 2014 +0400
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Oct 9 23:15:54 2014 -0700

    configure: Also check for Python 2.x installed as python2.7.
    
    On ArchLinux &quot;python&quot; points to 3.x version and the right
    2.x python binary is &quot;python2.7&quot;.
    
    Signed-off-by: Dmitry V. Krivenok &lt;krivenok.dmitry@gmail.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
