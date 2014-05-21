---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
42df0b12-3173-4e92-9bc3-0008a52bfdc1
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b86ea861-f36e-43a7-84ea-bb58151a2299
controller          : [974710a3-ed3a-4251-a3de-0075ce300c75]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [28920335-e96c-4279-8b9c-f82489959fda, 29a01b13-ebfe-401c-b533-127be87d7074, 2b5cb153-fab8-47b6-9b8e-9b756f3cfc9e, fb9b598a-59da-47f0-bb89-19574e44c4b6]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 974710a3-ed3a-4251-a3de-0075ce300c75
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=567, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 28920335-e96c-4279-8b9c-f82489959fda
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1a93b017-35c9-4680-9708-b8e24519e628]
name                : eth21

_uuid               : fb9b598a-59da-47f0-bb89-19574e44c4b6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3f8c657f-60bd-4cee-8570-b0aaa2a434d0]
name                : eth23

_uuid               : 2b5cb153-fab8-47b6-9b8e-9b756f3cfc9e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [937e6ede-cdaf-4241-aecf-60a925fb0467]
name                : eth22

_uuid               : 29a01b13-ebfe-401c-b533-127be87d7074
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2d4d8262-ef7e-4815-9976-ec0d203fc360]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 937e6ede-cdaf-4241-aecf-60a925fb0467
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1311898804, tx_dropped=0, tx_errors=0, tx_packets=878126}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2d4d8262-ef7e-4815-9976-ec0d203fc360
admin_state         : down
duplex              : full
ifindex             : 117
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

_uuid               : 3f8c657f-60bd-4cee-8570-b0aaa2a434d0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2334118500, tx_dropped=0, tx_errors=0, tx_packets=1556079}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 1a93b017-35c9-4680-9708-b8e24519e628
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
statistics          : {collisions=0, rx_bytes=3319056488, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2222042, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a0bab870f57d4a042cab2e0ed51ba929cb4013b8
Author:     Ryan Wilson &lt;wryan@nicira.com&gt;
AuthorDate: Tue May 20 21:50:19 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Tue May 20 22:03:35 2014 -0700

    ofproto: Remove per-flow miss hash table from upcall handler.
    
    The upcall handler keeps a hash table which hashes flow to a list
    of corresponding packets.  This used to be necessary as packets with
    the same flow had similar actions and calculating actions used to be
    a performance bottleneck.  Now that userspace action calculation
    performance has improved, there is no need for this hash map.
    
    This patch removes this hash map and each packet has its own upcall.
    
    Signed-off-by: Ryan Wilson &lt;wryan@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
