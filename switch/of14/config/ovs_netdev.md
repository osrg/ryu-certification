---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
25886b40-82dd-4330-83d5-df883ae97d05
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 32008ac9-aedf-43ba-942f-da329cf84edf
controller          : [4c49a332-f040-43ec-8cbb-ab88212c76ad]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [22fa3413-f667-49ed-9fc3-f7a50e2d6ddb, 43f0ca12-103a-4674-8bcb-c469d83088b7, ba76c645-ccb7-480a-acab-65ba4fe1f456, fd838144-2c6d-4ec5-af2b-082f41e3734d]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4c49a332-f040-43ec-8cbb-ab88212c76ad
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=781, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : fd838144-2c6d-4ec5-af2b-082f41e3734d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8ad4eab5-1d56-4405-9d96-2ed1d6bf8ef6]
name                : eth23

_uuid               : ba76c645-ccb7-480a-acab-65ba4fe1f456
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fdd5803f-5999-4f7d-86d4-73f2cdaf3ed5]
name                : br0

_uuid               : 43f0ca12-103a-4674-8bcb-c469d83088b7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c551400b-4370-4a83-86d4-8b30303f2086]
name                : eth22

_uuid               : 22fa3413-f667-49ed-9fc3-f7a50e2d6ddb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [403c51fa-e221-474e-a612-b0cce2e9e146]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8ad4eab5-1d56-4405-9d96-2ed1d6bf8ef6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3388027408, tx_dropped=0, tx_errors=0, tx_packets=7985308}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 403c51fa-e221-474e-a612-b0cce2e9e146
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
statistics          : {collisions=0, rx_bytes=2017276453, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=170372987, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : fdd5803f-5999-4f7d-86d4-73f2cdaf3ed5
admin_state         : down
duplex              : full
ifindex             : 271
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

_uuid               : c551400b-4370-4a83-86d4-8b30303f2086
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2361254052, tx_dropped=0, tx_errors=0, tx_packets=104695153}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 15fd90524b40dc7147fc4d8abd96630687ca3640
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Sat Oct 18 11:39:38 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Oct 21 12:35:11 2014 -0700

    netlink-socket: Fix nl_sock_recv__&#40;&#41; on Windows.
    
    In nl_sock_recv__&#40;&#41; on Windows, we realloc a new ofpbuf to copy received
    data if the caller specified buffer is small. While we do so, we need
    reset some of the other stack variables to point to the new ofpbuf.
    
    Other fixes are around using 'error' rather than 'errno'.
    
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Acked-by: Ankur Sharma &lt;ankursharma@vmware.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
