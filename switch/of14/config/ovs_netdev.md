---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d388fd31-e733-47c8-941e-e6cefab44a81
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 6b4286f7-63fc-4f29-8088-08193c0423c0
controller          : [76180661-6715-4d07-b0fe-0fd62f46f183]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4febd67e-6f84-4a17-a320-e88f8499d0b9, 934c56db-f0c4-4d1c-acf6-549903cd6b5b, a281b30c-9bc4-4a6b-84e5-87e7e8ef4597, bda9447a-2930-44c1-a507-10269f567221]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 76180661-6715-4d07-b0fe-0fd62f46f183
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=672, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a281b30c-9bc4-4a6b-84e5-87e7e8ef4597
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2f006662-760b-490f-8536-64b76a4e92b7]
name                : br0

_uuid               : bda9447a-2930-44c1-a507-10269f567221
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f70aa96c-c074-426c-bd6a-b8922c0e8365]
name                : eth21

_uuid               : 4febd67e-6f84-4a17-a320-e88f8499d0b9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2b823d55-8600-4845-aac5-c9fd448bf6f0]
name                : eth23

_uuid               : 934c56db-f0c4-4d1c-acf6-549903cd6b5b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [42658d12-cd4e-4376-8074-b34981719859]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f70aa96c-c074-426c-bd6a-b8922c0e8365
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
statistics          : {collisions=0, rx_bytes=3419943949, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=171315673, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2b823d55-8600-4845-aac5-c9fd448bf6f0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=145344612, tx_dropped=0, tx_errors=0, tx_packets=8686831}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 42658d12-cd4e-4376-8074-b34981719859
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2992028472, tx_dropped=0, tx_errors=0, tx_packets=105119184}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2f006662-760b-490f-8536-64b76a4e92b7
admin_state         : down
duplex              : full
ifindex             : 295
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ee4dac3bb6dcef43c51f7ddf3ad954eab4c9ed0f
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Tue Oct 28 10:01:22 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Oct 28 10:46:07 2014 -0700

    netdev-windows: Fix bugs in flag update and MAC address copy functions.
    
    The .update_flags function in netdev-windows was dummy. But we need to
    return the existing flags for link status to be shown as up in the
    confdb.
    
    There was a bug in copying the MAC address.
    
    We fix these two issues in this patch.
    
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Co-Authored-by: Ankur Sharma &lt;ankursharma@vmware.com&gt;
    Signed-off-by: Ankur Sharma &lt;ankursharma@vmware.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Tested-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
