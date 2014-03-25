---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ace360f0-6fe0-466b-b1c8-cce1502bca12
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
_uuid               : 8ac168e9-e0e7-40ec-b431-5456eec44158
controller          : [b277cbd9-8e9c-41e7-9142-cbdf227fb24c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [16a06d25-554a-45b2-93f7-3df1771ab4ad, c749e14b-ba66-4fb0-876c-1802bc1c043d, c88001b5-9c9b-47da-b82b-8c1b65c6c80e]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b277cbd9-8e9c-41e7-9142-cbdf227fb24c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=307, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c88001b5-9c9b-47da-b82b-8c1b65c6c80e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5a3f71c2-7276-427f-9510-6366fd5e78b8]
name                : eth7

_uuid               : 16a06d25-554a-45b2-93f7-3df1771ab4ad
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [558b88bf-4d0b-4c75-9972-af46b5a3804c]
name                : br0

_uuid               : c749e14b-ba66-4fb0-876c-1802bc1c043d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1979cd01-d01e-45d9-8a81-43564e67c812]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1979cd01-d01e-45d9-8a81-43564e67c812
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5487554, tx_dropped=0, tx_errors=0, tx_packets=58502}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 5a3f71c2-7276-427f-9510-6366fd5e78b8
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
statistics          : {collisions=0, rx_bytes=3069277790, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72696263, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 558b88bf-4d0b-4c75-9972-af46b5a3804c
admin_state         : up
duplex              : full
ifindex             : 728
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
commit f21fa45f30856d07b712661566ae8d1bcb62a31a
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Mar 25 12:35:28 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Mar 25 13:33:25 2014 -0700

    lockfile: Minor code cleanup.
    
    There were more superficial differences between Windows and non-Windows
    versions of the code due to naming.  This commit reduces those differences.
    
    CC: Gurucharan Shetty &lt;shettyg@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
