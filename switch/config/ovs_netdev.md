---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c6939fad-3924-4c78-b985-ba3eff948fa3
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ac048449-a684-4968-bbaf-790c339bfed8
controller          : [e2fce1e1-2a61-4dfb-9780-71bac17175d9]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [4cddba1a-0a54-426e-81ae-e0c5d57750e7, 5d09c390-5044-4e0d-b67e-efb622afb270, 61fc29ff-7d73-4a93-a03a-2f979841e2d6, 9315183f-7d29-4af1-8e6a-487b78017482]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e2fce1e1-2a61-4dfb-9780-71bac17175d9
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="4", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5d09c390-5044-4e0d-b67e-efb622afb270
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [369230bf-6664-4cd6-92bd-eefe5a354108]
name                : "eth22"

_uuid               : 4cddba1a-0a54-426e-81ae-e0c5d57750e7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4ded1d2a-f33e-41ff-8be2-bef7abd1b166]
name                : "eth23"

_uuid               : 9315183f-7d29-4af1-8e6a-487b78017482
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [caf308ca-b2e2-4039-bb5a-24842fb6ef87]
name                : "br0"

_uuid               : 61fc29ff-7d73-4a93-a03a-2f979841e2d6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e8cfc5d9-90b5-4ca0-b310-64a4c1750cfb]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e8cfc5d9-90b5-4ca0-b310-64a4c1750cfb
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
statistics          : {collisions=0, rx_bytes=1230673259236, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=820816009, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : caf308ca-b2e2-4039-bb5a-24842fb6ef87
admin_state         : down
duplex              : full
ifindex             : 879
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

_uuid               : 4ded1d2a-f33e-41ff-8be2-bef7abd1b166
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=40230934500, tx_dropped=0, tx_errors=0, tx_packets=26820623}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 369230bf-6664-4cd6-92bd-eefe5a354108
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=629732972082, tx_dropped=0, tx_errors=0, tx_packets=419983393}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5f5ebd4cc8bfede3410fbb5db574693eae8c29e0
Author:     Flavio Leitner &lt;fbl@redhat.com&gt;
AuthorDate: Wed Apr 8 14:30:40 2015 -0300
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Thu Apr 9 10:19:55 2015 -0700

    testsuite: ofproto-dpif: fix test names
    
    Some tests were not included when running the
    make TESTSUITEFLAGS=&quot;-k ofproto-dpif&quot; check because
    the test name was out of the expected pattern.
    
    Signed-off-by: Flavio Leitner &lt;fbl@redhat.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
