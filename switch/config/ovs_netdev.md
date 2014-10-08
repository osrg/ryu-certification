---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e0ea2de4-801a-4547-be36-0928288d74b0
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0f94914c-dff4-4313-b737-1fa31317e6b3
controller          : [6340d71d-8609-4a35-b7c1-02105e556df6]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0d2f4b17-a904-4f90-82d0-1f0121e07481, 1e3db6af-42c1-4a9b-a33b-c2928869189a, 82f5919e-ec96-41de-a177-560882c49bed, c4c8b9dc-cf23-4888-9c59-232d25e25994]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6340d71d-8609-4a35-b7c1-02105e556df6
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=692, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c4c8b9dc-cf23-4888-9c59-232d25e25994
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [29c6d04a-eba6-4017-9600-7b59eff30e23]
name                : br0

_uuid               : 82f5919e-ec96-41de-a177-560882c49bed
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9aa5d242-8f8f-40d8-b2e0-73522fb299d2]
name                : eth23

_uuid               : 0d2f4b17-a904-4f90-82d0-1f0121e07481
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4793a22d-ec92-4e05-8716-cabb13b3f17f]
name                : eth22

_uuid               : 1e3db6af-42c1-4a9b-a33b-c2928869189a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [47615b99-e4cc-48e1-a7fd-d79bafcb3b59]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4793a22d-ec92-4e05-8716-cabb13b3f17f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1615029624, tx_dropped=0, tx_errors=0, tx_packets=72692294}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 47615b99-e4cc-48e1-a7fd-d79bafcb3b59
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
statistics          : {collisions=0, rx_bytes=291892031, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=123390052, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 29c6d04a-eba6-4017-9600-7b59eff30e23
admin_state         : down
duplex              : full
ifindex             : 219
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

_uuid               : 9aa5d242-8f8f-40d8-b2e0-73522fb299d2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=865922908, tx_dropped=0, tx_errors=0, tx_packets=6303905}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ff8debff85f864767ed5cd61c231f6d97d95d680
Author:     Alin Serdean &lt;aserdean@cloudbasesolutions.com&gt;
AuthorDate: Wed Oct 8 17:50:47 2014 +0000
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Oct 8 10:55:20 2014 -0700

    Add meta-flow.inc nx-match.inc to lib/.gitignore
    
    Add the following files:
    meta-flow.inc
    nx-match.inc
    to lib/.gitignore
    
    Signed-off-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
