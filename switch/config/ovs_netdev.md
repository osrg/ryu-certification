---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
42958287-667d-4148-ac0d-33cbf44d8989
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
_uuid               : cdf20e80-ba81-4b46-83de-0d5ca38744fe
controller          : [2813d8bf-810b-4aa9-a14e-a2016d07d2ef]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [b118536f-7888-46f7-9d4b-b1f45872bba6, d9b2ddda-9524-4807-a604-6d95d7cf0d38, d9b6766a-1eb6-421e-9114-eb522c812be4]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2813d8bf-810b-4aa9-a14e-a2016d07d2ef
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=377, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d9b2ddda-9524-4807-a604-6d95d7cf0d38
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [10bd95b7-972e-43ef-8b2d-cf8ca7f580d8]
name                : eth7

_uuid               : d9b6766a-1eb6-421e-9114-eb522c812be4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [613b1c70-ed8a-4c50-816e-2b573b5f07d3]
name                : br0

_uuid               : b118536f-7888-46f7-9d4b-b1f45872bba6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1f19a386-688e-49d9-b2cb-4bc6a0f5beb2]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 613b1c70-ed8a-4c50-816e-2b573b5f07d3
admin_state         : up
duplex              : full
ifindex             : 330
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

_uuid               : 1f19a386-688e-49d9-b2cb-4bc6a0f5beb2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2628690, tx_dropped=0, tx_errors=0, tx_packets=28062}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 10bd95b7-972e-43ef-8b2d-cf8ca7f580d8
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
statistics          : {collisions=0, rx_bytes=3059565659, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72597713, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0c0c32d825d0fa392db834e7d57864e878134a72
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Feb 21 12:40:00 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Feb 21 12:40:00 2014 -0800

    ofproto-dpif: Fix segfault removing port when STP is enabled.
    
    Reported-by: Sridhar Samudrala &lt;samudrala.sridhar@gmail.com&gt;
    Tested-by: Sridhar Samudrala &lt;samudrala.sridhar@gmail.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
