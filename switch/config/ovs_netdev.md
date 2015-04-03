---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8603891d-9783-4863-966c-87ae4026bb8b
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
_uuid               : d407e751-da65-4f93-a729-8bb2dd4475eb
controller          : [5dd5eb07-2abd-4c22-80ab-80cea05689e6]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [4f57b89b-b455-4b9a-a5a4-9c4a7f4126de, 5d2d1399-c74c-4419-90f3-dcb0417581d0, 61a8c24c-cbcd-4685-bb6f-4413cef8648b, e3c21d84-eeb5-421d-a94a-3cc46a58abcb]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5dd5eb07-2abd-4c22-80ab-80cea05689e6
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="656", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 61a8c24c-cbcd-4685-bb6f-4413cef8648b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [add9f6cf-5ecd-4d23-acd8-a317af7e24b0]
name                : "br0"

_uuid               : e3c21d84-eeb5-421d-a94a-3cc46a58abcb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [52c954b1-032f-4621-bc07-c3ccf2ffd00f]
name                : "eth21"

_uuid               : 5d2d1399-c74c-4419-90f3-dcb0417581d0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [868253c9-e023-4176-b34f-b041ae268a0c]
name                : "eth23"

_uuid               : 4f57b89b-b455-4b9a-a5a4-9c4a7f4126de
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [455807d7-5550-4b1f-9cf7-ba93a0466004]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 52c954b1-032f-4621-bc07-c3ccf2ffd00f
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
statistics          : {collisions=0, rx_bytes=1217807252202, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=812229139, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 868253c9-e023-4176-b34f-b041ae268a0c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=39090214500, tx_dropped=0, tx_errors=0, tx_packets=26060143}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 455807d7-5550-4b1f-9cf7-ba93a0466004
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=619449025276, tx_dropped=0, tx_errors=0, tx_packets=413123111}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : add9f6cf-5ecd-4d23-acd8-a317af7e24b0
admin_state         : down
duplex              : full
ifindex             : 852
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
commit 4f7e5c274bfff6187313588a66491bcf45b7a709
Author:     Russell Bryant &lt;rbryant@redhat.com&gt;
AuthorDate: Thu Apr 2 17:51:49 2015 -0400
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Apr 2 19:15:52 2015 -0700

    INSTALL.md: Add note about EXTRA_CFLAGS.
    
    Add a note about the use of EXTRA_CFLAGS to provide custom CFLAGS for
    the build of the Linux kernel module.
    
    This addition is technically in the &quot;configuring the sources&quot; section
    of the document.  However, it's the spot where custom CFLAGS is
    discussed already, so that seemed like the best place to put it.
    Alternatively, it could go in the &quot;Building the Sources&quot; section
    instead.
    
    Signed-off-by: Russell Bryant &lt;rbryant@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
