---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ed4d48c3-79df-4a93-913b-70f86b2a08eb
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0c489186-e8cd-4c50-86d0-a7fedd546d97
controller          : [5f0f2d8d-5689-479c-99eb-6cd55f9c6f34]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [a4e970df-4391-4b57-b966-7152966266f3, c6fd87bb-2063-4d00-8443-2f6cd1deb252, cf315fcb-5d8e-4258-847b-841d4e321826, e59eed2f-f73b-4a2e-85c1-63853f6ae7bb]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5f0f2d8d-5689-479c-99eb-6cd55f9c6f34
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="762", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c6fd87bb-2063-4d00-8443-2f6cd1deb252
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [10e120e6-ed29-4c12-9254-80ba48b02508]
name                : "eth22"

_uuid               : cf315fcb-5d8e-4258-847b-841d4e321826
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [46418d8f-47b5-4ebd-9fd1-772e615dbc7e]
name                : "br0"

_uuid               : e59eed2f-f73b-4a2e-85c1-63853f6ae7bb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [29d0dbc1-974a-4dd9-8925-1d580ecfc9f7]
name                : "eth23"

_uuid               : a4e970df-4391-4b57-b966-7152966266f3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [49cc1955-eab0-46cd-be72-0ea0a7611140]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 29d0dbc1-974a-4dd9-8925-1d580ecfc9f7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5111125500, tx_dropped=0, tx_errors=0, tx_packets=3407417}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 49cc1955-eab0-46cd-be72-0ea0a7611140
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
statistics          : {collisions=0, rx_bytes=40535386059, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27063065, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 10e120e6-ed29-4c12-9254-80ba48b02508
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28403012344, tx_dropped=0, tx_errors=0, tx_packets=18952664}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 46418d8f-47b5-4ebd-9fd1-772e615dbc7e
admin_state         : down
duplex              : full
ifindex             : 619
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
commit 0df6430eda565058a297f911fefec7e6f6bbe34f
Author:     Russell Bryant &lt;rbryant@redhat.com&gt;
AuthorDate: Wed Oct 21 16:13:43 2015 -0400
Commit:     Russell Bryant &lt;rbryant@redhat.com&gt;
CommitDate: Wed Nov 4 11:03:18 2015 -0500

    ovn-tutorial: Add a section on ACLs.
    
    Add a section that gives a quick introduction to applying ACLs.  It
    discusses how the ACLs are translated into OVN logical flows. It doesn't
    get down to the OpenFlow level because that's not supported in
    ovs-sandbox yet.  Instead, it provides a reference to an OpenStack
    related blog post that talks about how OVN ACLs are used there and gives
    examples of the resulting OpenFlow flows.
    
    In theory, once we have a userspace conntrack implementation available,
    we'll be able to provide better suppot for it in ovs-sandbox.
    
    Signed-off-by: Russell Bryant &lt;rbryant@redhat.com&gt;
    Acked-by: Kyle Mestery &lt;mestery@mestery.com&gt;
</pre>
