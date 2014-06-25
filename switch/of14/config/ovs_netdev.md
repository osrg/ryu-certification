---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
76c1c7dd-898a-4883-8446-d9c8b2c8e05d
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
_uuid               : 286eee80-e4e1-4fbb-8211-abe772e9cd06
controller          : [dd650501-1d6c-4c3e-8d70-5fa95d93912a]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1fbcb327-8253-4b4a-9a8b-728ca5dbc201, 227a5ce3-65ac-45b7-9205-664b52ba1990, 5458797e-982e-4d98-8c7b-43d133fea0d5, f64b07e6-c8a0-49c7-a984-44527e912648]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : dd650501-1d6c-4c3e-8d70-5fa95d93912a
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=977, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5458797e-982e-4d98-8c7b-43d133fea0d5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [239eb704-3706-4773-9e46-abf253c914c3]
name                : eth22

_uuid               : f64b07e6-c8a0-49c7-a984-44527e912648
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [461d85d8-d5fa-47ae-8b2b-18dbf4428d96]
name                : eth23

_uuid               : 227a5ce3-65ac-45b7-9205-664b52ba1990
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c69bb716-414f-441e-b34e-a3bb40798e62]
name                : br0

_uuid               : 1fbcb327-8253-4b4a-9a8b-728ca5dbc201
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ef0832b4-08e4-4856-9b8f-c5f2842d5ef3]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ef0832b4-08e4-4856-9b8f-c5f2842d5ef3
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
statistics          : {collisions=0, rx_bytes=4039232540, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=91592134, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 239eb704-3706-4773-9e46-abf253c914c3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2424532546, tx_dropped=0, tx_errors=0, tx_packets=36028564}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 461d85d8-d5fa-47ae-8b2b-18dbf4428d96
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2014570284, tx_dropped=0, tx_errors=0, tx_packets=12796977}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c69bb716-414f-441e-b34e-a3bb40798e62
admin_state         : down
duplex              : full
ifindex             : 702
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
commit 7b7c2a463d4a56c33bfb8466b8dc3b6de9494991
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed Jun 25 11:39:25 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jun 25 11:39:25 2014 -0700

    json: Fix parsing of strings that end with a backslash.
    
    json_string_unescape&#40;&#41; flagged a backslash at the end of a string as an
    error, but of course &quot;\&quot; is a valid string.  This fixes the problem.
    
    VMware-BZ: #1275208
    Reported-by: Michael Hu &lt;mhu@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
