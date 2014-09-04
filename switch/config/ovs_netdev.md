---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
80065d94-de25-4a81-8822-314914f21be7
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7aeff1fc-3358-4c54-85d0-2c02b9694990
controller          : [7c0eac6e-b8f4-4151-954e-8f2009c5a497]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [3ed7a6b7-a16d-4a90-ab06-1dacc51297e3, 8b3ad96a-e66f-489f-bde8-2457dd035da0, b4c36be3-32e3-4eab-8c38-737fa530fbec, cfc4be18-366e-4eb2-811b-0d5a44137798]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7c0eac6e-b8f4-4151-954e-8f2009c5a497
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=662, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : cfc4be18-366e-4eb2-811b-0d5a44137798
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b711bea3-c403-4bd3-83ad-2209b142e2f5]
name                : eth22

_uuid               : 8b3ad96a-e66f-489f-bde8-2457dd035da0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2ebbd5dd-3f6a-4dc0-a2bc-d2415025c240]
name                : br0

_uuid               : 3ed7a6b7-a16d-4a90-ab06-1dacc51297e3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1d8d32f0-fa14-4c20-adbd-09eb74789c7d]
name                : eth23

_uuid               : b4c36be3-32e3-4eab-8c38-737fa530fbec
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4e4f9784-0fd5-4bbf-8dea-ef5074cf5e13]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1d8d32f0-fa14-4c20-adbd-09eb74789c7d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3344205000, tx_dropped=0, tx_errors=0, tx_packets=2229470}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 4e4f9784-0fd5-4bbf-8dea-ef5074cf5e13
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
statistics          : {collisions=0, rx_bytes=2859765362, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=33427000, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2ebbd5dd-3f6a-4dc0-a2bc-d2415025c240
admin_state         : down
duplex              : full
ifindex             : 92
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

_uuid               : b711bea3-c403-4bd3-83ad-2209b142e2f5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1268645420, tx_dropped=0, tx_errors=0, tx_packets=23763126}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6524e997ec55bace8515a35e552653814b128d1a
Author:     Ankur Sharma &lt;ankursharma@vmware.com&gt;
AuthorDate: Wed Sep 3 16:33:40 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Sep 4 09:43:15 2014 -0700

    datapath-windows: NetlinkBuf.c: Minor fix for lines exceeding 79 chars
    
    Signed-off-by: Ankur Sharma &lt;ankursharma@vmware.com&gt;
    Tested-by: Ankur Sharma &lt;ankursharma@vmware.com&gt;
    Reported-at: https://github.com/openvswitch/ovs-issues/issues/37
    Acked-by: Eitan Eliahu &lt;eliahue@vmware.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean at cloudbasesolutions.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
