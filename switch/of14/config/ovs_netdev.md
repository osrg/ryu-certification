---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0dcdaf86-5464-44d2-92b6-bf4e81179a3e
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 25552537-146a-4115-8758-239bee67a5f2
controller          : [322bc807-a83a-4ad9-bd83-c17d0f667e4f]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [09e5abe1-c985-49bc-9b68-7e098789c542, 3b1337b3-28d4-42f3-bf56-a4ab40fd63cf, 69b95654-68f1-4e53-90d8-16a76d3a2559, b67d0869-bcd7-484e-b9b3-904a9c2c4f01]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 322bc807-a83a-4ad9-bd83-c17d0f667e4f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=671, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 69b95654-68f1-4e53-90d8-16a76d3a2559
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d21badfb-a7d4-4649-81d1-21a81537d8ca]
name                : eth21

_uuid               : 09e5abe1-c985-49bc-9b68-7e098789c542
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7172f198-dffe-4727-ba4e-03a6147752f1]
name                : eth22

_uuid               : b67d0869-bcd7-484e-b9b3-904a9c2c4f01
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4deba30c-c2c2-4990-9241-d32c46c994c8]
name                : br0

_uuid               : 3b1337b3-28d4-42f3-bf56-a4ab40fd63cf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [894a23a8-5308-411a-bb37-e6945cb1c53f]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4deba30c-c2c2-4990-9241-d32c46c994c8
admin_state         : down
duplex              : full
ifindex             : 287
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

_uuid               : 894a23a8-5308-411a-bb37-e6945cb1c53f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4089829408, tx_dropped=0, tx_errors=0, tx_packets=8453176}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 7172f198-dffe-4727-ba4e-03a6147752f1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2781469832, tx_dropped=0, tx_errors=0, tx_packets=104977640}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d21badfb-a7d4-4649-81d1-21a81537d8ca
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
statistics          : {collisions=0, rx_bytes=2952375617, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=171001436, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 8341662d1b57edc90e7bbc020319b282ca7f3ab2
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Fri Oct 24 08:14:52 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Oct 24 16:49:31 2014 -0700

    netlink-socket: Fix a couple of compilation warnings.
    
    Reported-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Tested-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    [blp@nicira.com replaced conventional cast by CONST_CAST]
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
