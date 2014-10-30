---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
aeaf301a-52ca-4b4a-9654-cc8d9b3fe38a
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
_uuid               : 8eb5294c-1909-488c-b26c-bb8e68b58fd6
controller          : [5448695e-ba26-4604-a11a-de2d649d911f]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [28210802-e0a7-437f-95c1-f26d55594236, 290590aa-0086-464d-9a6d-6f6e872a2ca1, 2f950722-a17d-451d-a978-dbafb64e6b20, 7886a176-fb1b-43ff-a1bf-81de995822bf]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5448695e-ba26-4604-a11a-de2d649d911f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=802, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2f950722-a17d-451d-a978-dbafb64e6b20
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0dafb4c7-9674-4b64-9c61-4d6729ea9272]
name                : eth22

_uuid               : 28210802-e0a7-437f-95c1-f26d55594236
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b79e3b88-e98e-4f9c-8dd9-c731ef067778]
name                : eth21

_uuid               : 7886a176-fb1b-43ff-a1bf-81de995822bf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [beb689a4-1fdd-4652-8bd1-3206438dbf35]
name                : eth23

_uuid               : 290590aa-0086-464d-9a6d-6f6e872a2ca1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5822f53d-409c-416c-975f-fafb47daa011]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : beb689a4-1fdd-4652-8bd1-3206438dbf35
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=13420008000, tx_dropped=0, tx_errors=0, tx_packets=8946672}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b79e3b88-e98e-4f9c-8dd9-c731ef067778
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
statistics          : {collisions=0, rx_bytes=257384137513, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=171692466, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 5822f53d-409c-416c-975f-fafb47daa011
admin_state         : down
duplex              : full
ifindex             : 303
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

_uuid               : 0dafb4c7-9674-4b64-9c61-4d6729ea9272
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=157894353712, tx_dropped=0, tx_errors=0, tx_packets=105309462}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 03ec3f12967349d5f744f18c71f2a81487da6117
Author:     Wang Sheng-Hui &lt;shhuiw@gmail.com&gt;
AuthorDate: Thu Oct 30 12:55:33 2014 +0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Oct 30 10:24:05 2014 -0700

    tests: Check the existance of WHY-OVS.md instead of WHY-OVS.
    
    WHY-OVS has been renamed to WHY-OVS.md. Update the filenames in run-oftest
    and run-ryu scripts
    
    Signed-off-by: Wang Sheng-Hui &lt;shhuiw@gmail.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
