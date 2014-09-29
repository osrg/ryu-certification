---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6a0b85d5-68da-4b3d-b6ba-2b1eac41651a
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
_uuid               : 02f5e20b-b196-47a1-9c60-2448d1f5ff20
controller          : [cf170328-67e8-4e54-b875-60400139ba6b]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2089316f-ec9a-4347-ba19-3e454a9c9734, 74dcc91c-f072-472d-997a-d611226a3b88, 81e2be26-1863-413d-ac00-111a286e957b, d57662f1-639a-438d-bc3f-2cda9f3aaac8]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : cf170328-67e8-4e54-b875-60400139ba6b
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=681, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 74dcc91c-f072-472d-997a-d611226a3b88
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e464e6a6-880c-4aac-9096-4195a7ecd59e]
name                : eth22

_uuid               : d57662f1-639a-438d-bc3f-2cda9f3aaac8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a3521e6f-4a0a-4d5b-b173-c13da40b3a86]
name                : eth21

_uuid               : 81e2be26-1863-413d-ac00-111a286e957b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0d5cb526-f446-4557-a9d9-9f88950b5f01]
name                : br0

_uuid               : 2089316f-ec9a-4347-ba19-3e454a9c9734
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [15ad22cd-e2cc-4215-bad4-e50684e3a281]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 15ad22cd-e2cc-4215-bad4-e50684e3a281
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3378498704, tx_dropped=0, tx_errors=0, tx_packets=5115644}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e464e6a6-880c-4aac-9096-4195a7ecd59e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2834169682, tx_dropped=0, tx_errors=0, tx_packets=47728279}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0d5cb526-f446-4557-a9d9-9f88950b5f01
admin_state         : down
duplex              : full
ifindex             : 184
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

_uuid               : a3521e6f-4a0a-4d5b-b173-c13da40b3a86
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
statistics          : {collisions=0, rx_bytes=1426084481, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=75453865, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 09853482b9c3e067a838918b3ee3ecc23cf529f6
Author:     Ankur Sharma &lt;ankursharma@vmware.com&gt;
AuthorDate: Mon Sep 29 10:13:00 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Sep 29 11:11:21 2014 -0700

    datapath-windows: Build fix.
    
    Recently we changed the signature of NlAttrParse.
    Function OvsGetVport was not updated accordingly.
    
    Fixed the same.
    
    Signed-off-by: Ankur Sharma &lt;ankursharma@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Eitan Eliahu &lt;eliahue@vmware.com&gt;
    Acked-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
</pre>
