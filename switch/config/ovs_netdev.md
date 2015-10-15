---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
15c8026f-e99c-4f1b-81c6-6aaceb9befbd
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 24d687a5-519b-4e94-9097-0c4c56a90b30
controller          : [3c53092c-699c-467e-a0f1-ce406114df0c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2ddc9724-f2e4-4c88-89e8-f89083472077, 459fb01c-b913-485e-af14-006c6853801e, 7f3b3c89-31a1-4ae3-8af3-eb494b266c2c, f0b22d91-4863-4b53-8429-01484752c587]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3c53092c-699c-467e-a0f1-ce406114df0c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="752", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2ddc9724-f2e4-4c88-89e8-f89083472077
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [275a6d21-961e-4506-9cb1-84a1adc57742]
name                : "eth21"

_uuid               : 459fb01c-b913-485e-af14-006c6853801e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ecec8dc4-0f7c-4cd5-af41-d1ffa161f3ec]
name                : "eth23"

_uuid               : 7f3b3c89-31a1-4ae3-8af3-eb494b266c2c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f59387c7-a852-4a99-8c32-0608aec57e12]
name                : "br0"

_uuid               : f0b22d91-4863-4b53-8429-01484752c587
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3864d9aa-94fa-4f72-8dcb-07e4dbe3eac0]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ecec8dc4-0f7c-4cd5-af41-d1ffa161f3ec
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3094116000, tx_dropped=0, tx_errors=0, tx_packets=2062744}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 275a6d21-961e-4506-9cb1-84a1adc57742
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
statistics          : {collisions=0, rx_bytes=37843950238, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=25253963, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 3864d9aa-94fa-4f72-8dcb-07e4dbe3eac0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=27191328976, tx_dropped=0, tx_errors=0, tx_packets=18138529}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f59387c7-a852-4a99-8c32-0608aec57e12
admin_state         : down
duplex              : full
ifindex             : 567
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 38b366b1c3f5ca3f8b96782af6432f77c48cb2c9
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Thu Oct 15 09:19:11 2015 -0700
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Thu Oct 15 09:22:17 2015 -0700

    vswitch.xml: Add caveat to flow-limit.
    
    This option should only be tweaked by developers investigating the
    behaviour of flow caching, so recommend that this option is not used.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
