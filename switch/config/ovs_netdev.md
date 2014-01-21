---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6cba2d48-2758-4d60-a8ae-b3abbce53843
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 41c05566-4f22-496f-9d2f-4518d04614e7
controller          : [a88c4aa1-f6a7-4803-b2d0-dd89e153030e]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0e3b2b76-1270-45f1-b4ae-44983e950d54, 2edebe30-a679-42ab-9a8a-311506bb4b4f, acab9e35-880d-475e-b23a-4cc55a7684f7]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a88c4aa1-f6a7-4803-b2d0-dd89e153030e
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=302, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2edebe30-a679-42ab-9a8a-311506bb4b4f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8f109489-7a78-40d8-81ab-a0b9453197d6]
name                : eth7

_uuid               : acab9e35-880d-475e-b23a-4cc55a7684f7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [866749f8-528e-4c7a-bfc0-53b13f464126]
name                : br0

_uuid               : 0e3b2b76-1270-45f1-b4ae-44983e950d54
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5789bd1a-af15-4173-9a78-e5a9cfaf2373]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 866749f8-528e-4c7a-bfc0-53b13f464126
admin_state         : up
duplex              : full
ifindex             : 123
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

_uuid               : 8f109489-7a78-40d8-81ab-a0b9453197d6
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
statistics          : {collisions=0, rx_bytes=2336175720, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1587042, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 5789bd1a-af15-4173-9a78-e5a9cfaf2373
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=995772, tx_dropped=0, tx_errors=0, tx_packets=10704}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit dfe37e6abd276de01f686bbdf28cbf48e92cd1dc
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Tue Jan 21 14:23:27 2014 -0800
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Tue Jan 21 14:24:06 2014 -0800

    bfd: Add bfd_src_ip and bfd_dst_ip.
    
    This commit adds two new options, bfd_src_ip and bfd_dst_ip
    respectively, which allows user to configure the source and
    destination IP address of bfd control packet.  If the user
    specified address cannot be parsed, the default address
    will be used.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
