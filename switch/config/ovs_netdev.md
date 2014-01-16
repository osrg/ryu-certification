---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f91af66f-6dc6-43dd-ae50-898c7a429e68
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 40a0d695-461c-46c0-bfb1-57c8c5419e48
controller          : [2bc1dca7-73eb-4f25-b113-33d3a08708d0]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [375f32f0-05ae-4fe4-8f49-d27da4ee3bd5, 526bef4c-e64c-454c-bddb-a25b5f8d582e, ca9f30cb-7b33-4438-b546-c0732f3c967d]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2bc1dca7-73eb-4f25-b113-33d3a08708d0
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=301, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 375f32f0-05ae-4fe4-8f49-d27da4ee3bd5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8f01f2d5-e045-427f-9812-634b6c9d3a57]
name                : br0

_uuid               : 526bef4c-e64c-454c-bddb-a25b5f8d582e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [500a3999-521f-4c74-ac86-7b6ea86b0fc4]
name                : eth8

_uuid               : ca9f30cb-7b33-4438-b546-c0732f3c967d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [93a60db7-585d-4062-b4f5-f3fbaf7bccf5]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8f01f2d5-e045-427f-9812-634b6c9d3a57
admin_state         : up
duplex              : full
ifindex             : 99
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

_uuid               : 500a3999-521f-4c74-ac86-7b6ea86b0fc4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=737160, tx_dropped=0, tx_errors=0, tx_packets=7938}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 93a60db7-585d-4062-b4f5-f3fbaf7bccf5
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
statistics          : {collisions=0, rx_bytes=2349540, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=23760, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit b73c85181df9cc38231a42d6f8095dcb604d230a
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Wed Jan 15 17:17:02 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jan 16 15:09:14 2014 -0800

    netdev-linux: Read packet auxdata to obtain vlan_tid
    
    If VLAN acceleration is used when the kernel receives a packet
    then the outer-most VLAN tag will not be present in the packet
    when it is received by netdev-linux. Rather, it will be present
    in auxdata.
    
    This patch uses recvmsg() instead of recv() to read auxdata for
    each packet and if the vlan_tid is set then it is added to the packet.
    
    Adding the vlan_tid makes use of headroom available
    in the buffer parameter of rx_recv.
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Co-authored-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
