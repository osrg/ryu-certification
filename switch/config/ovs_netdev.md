---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
bfaf4295-41ce-4f39-ad39-8782e0804ce9
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a78bb0ac-291c-43b4-92d5-eaf66bcd44af
controller          : [0b39e766-d730-446a-8e30-8583d674904b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2aa0ff2d-df78-4cb1-a495-85dda12a5026, 3294c067-b407-4f9f-ac00-2f1e1d1bd9ff, 8a1f2ca4-adf4-42aa-b244-29b74c034734, c257ff1d-1813-483f-b461-a171b00f871f]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0b39e766-d730-446a-8e30-8583d674904b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="657", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8a1f2ca4-adf4-42aa-b244-29b74c034734
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [35429a6e-bceb-422c-ae45-8d821d9ca57c]
name                : "br0"

_uuid               : 2aa0ff2d-df78-4cb1-a495-85dda12a5026
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bc0d9284-98a4-4cc0-87e4-e4b8d6415b8a]
name                : "eth22"

_uuid               : c257ff1d-1813-483f-b461-a171b00f871f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [80f1b33d-6c5a-4b41-8477-ec4231f993b9]
name                : "eth21"

_uuid               : 3294c067-b407-4f9f-ac00-2f1e1d1bd9ff
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d555ad77-cbb1-4076-b2bc-8d6389fc005e]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : bc0d9284-98a4-4cc0-87e4-e4b8d6415b8a
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=629627804528, tx_dropped=0, tx_errors=0, tx_packets=419912673}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 80f1b33d-6c5a-4b41-8477-ec4231f993b9
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=1230439389586, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=820658811, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 35429a6e-bceb-422c-ae45-8d821d9ca57c
admin_state         : down
duplex              : full
ifindex             : 875
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : d555ad77-cbb1-4076-b2bc-8d6389fc005e
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=40055503500, tx_dropped=0, tx_errors=0, tx_packets=26703669}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 46e7137c77d845c488e17b718eac7c3fb97cedcc
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Tue Apr 7 18:55:54 2015 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Tue Apr 7 19:00:17 2015 -0700

    geneve: Zero header before parsing userspace tunneling action.
    
    When we parse the text representation of the Geneve action the
    header is not fully initialized. Besides the obvious potential
    to generate an action that the user did not actually specify, this
    also causes intermittent unit test failures when an action is
    read in and printed out and the result is different.
    
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
