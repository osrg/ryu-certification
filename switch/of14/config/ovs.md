---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1bbdeaca-88dd-4a76-803a-350ebcf4ae78
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ec818033-4e05-4258-917e-4104e73d206a
controller          : [22e16a49-c2c2-403d-a55b-422236abec49]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [61e145df-fbeb-4cae-890a-fe3a21d81c9d, b9609740-7d25-45ec-a686-161c0b4c53ff, ba2a2290-3878-427b-ae97-936d18eff1b7, c72869fc-6ac3-4dc2-ab00-f7adf0501460]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 22e16a49-c2c2-403d-a55b-422236abec49
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=972, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c72869fc-6ac3-4dc2-ab00-f7adf0501460
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fb3fa297-f1d5-4acd-ad2c-27669bf9a4ea]
name                : eth22

_uuid               : ba2a2290-3878-427b-ae97-936d18eff1b7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8718b1bd-4154-4484-8991-baafeb1cc73c]
name                : eth23

_uuid               : b9609740-7d25-45ec-a686-161c0b4c53ff
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [48a99532-da81-4b77-a69f-9a19d18d96b7]
name                : br0

_uuid               : 61e145df-fbeb-4cae-890a-fe3a21d81c9d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fae6b217-7c36-41a5-ba96-891eed0f9b98]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8718b1bd-4154-4484-8991-baafeb1cc73c
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2213179284, tx_dropped=0, tx_errors=0, tx_packets=12929383}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 48a99532-da81-4b77-a69f-9a19d18d96b7
admin_state         : down
ifindex             : 706
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : fb3fa297-f1d5-4acd-ad2c-27669bf9a4ea
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2506449714, tx_dropped=0, tx_errors=0, tx_packets=36083639}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : fae6b217-7c36-41a5-ba96-891eed0f9b98
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
statistics          : {collisions=0, rx_bytes=4273043032, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=91749269, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
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
