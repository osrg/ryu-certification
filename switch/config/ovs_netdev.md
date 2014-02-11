---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
adf361b3-5d3b-42fb-84c6-5e3c9a154b10
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : fa8db98b-bd92-4887-9b86-1702a9cd60c9
controller          : [59237a5f-648f-46ff-812a-0ad3076ea6a7]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2d560973-95b3-47ab-a9e6-2e7142680f8c, a6a37710-1cf5-4692-9b8c-009eef2af3d6, c3926230-fc42-4d11-94ea-3dc053ece0ea]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 59237a5f-648f-46ff-812a-0ad3076ea6a7
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=297, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a6a37710-1cf5-4692-9b8c-009eef2af3d6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [796ec8b6-d981-4547-b4ad-28feb500b52f]
name                : br0

_uuid               : c3926230-fc42-4d11-94ea-3dc053ece0ea
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c0766114-8290-4c80-8c2b-70bebeed1ddb]
name                : eth7

_uuid               : 2d560973-95b3-47ab-a9e6-2e7142680f8c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [776cc791-0a81-4999-9336-9ba40823d715]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c0766114-8290-4c80-8c2b-70bebeed1ddb
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=3056453962, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72566276, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 776cc791-0a81-4999-9336-9ba40823d715
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1646274, tx_dropped=0, tx_errors=0, tx_packets=17585}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 796ec8b6-d981-4547-b4ad-28feb500b52f
admin_state         : up
duplex              : full
ifindex             : 220
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 276e2864c517a13f9a3ba33086b091743096d30c
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Feb 4 09:01:16 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Feb 11 07:55:38 2014 -0800

    pcap-file: Allow capturing TCP streams where the SYN is not seen.
    
    Until now, the tcp_stream() code has ignored any TCP packets that don't
    correspond to a stream that began with a TCP SYN.  This commit changes the
    code so that any TCP packet that contains a payload starts a new stream.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Reported-by: Vasu Dasari &lt;vdasari@gmail.com&gt;
</pre>
