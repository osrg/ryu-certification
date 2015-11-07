---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8057c82e-ac47-4fbb-8d25-ac950500d0b3
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 34eb12b4-8474-4d9d-93a9-5262e3489b33
controller          : [9d3b4041-af2c-4a5f-a1ff-6e3867c2971b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [416b59c8-35dd-4d3f-89cc-2467bdd340ae, 88944963-8727-43f3-ad6d-9027a1a40785, 8c11b8b2-f1f7-4fe6-877e-60bdad957169, ad640b79-6edd-46e4-aebd-27fe5311c065]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9d3b4041-af2c-4a5f-a1ff-6e3867c2971b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 416b59c8-35dd-4d3f-89cc-2467bdd340ae
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [df2a9fd3-f3f2-48d0-9420-7d3eeb961ada]
name                : "eth23"

_uuid               : ad640b79-6edd-46e4-aebd-27fe5311c065
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8bc714e8-535d-4f9d-a967-763fd4e6d0d9]
name                : "br0"

_uuid               : 8c11b8b2-f1f7-4fe6-877e-60bdad957169
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [23414d4d-83ff-4aed-95f2-b0a2ca1e88de]
name                : "eth22"

_uuid               : 88944963-8727-43f3-ad6d-9027a1a40785
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9d753cc4-b5c9-4dfb-81a5-f6abcd36d906]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8bc714e8-535d-4f9d-a967-763fd4e6d0d9
admin_state         : down
duplex              : full
ifindex             : 630
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

_uuid               : 9d753cc4-b5c9-4dfb-81a5-f6abcd36d906
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
statistics          : {collisions=0, rx_bytes=40874627571, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27290942, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 23414d4d-83ff-4aed-95f2-b0a2ca1e88de
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28592539564, tx_dropped=0, tx_errors=0, tx_packets=19079791}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : df2a9fd3-f3f2-48d0-9420-7d3eeb961ada
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5328567000, tx_dropped=0, tx_errors=0, tx_packets=3552378}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 607c5e55ae403763b7c0d7df262637c53135cd76
Author:     Justin Pettit &lt;jpettit@ovn.org&gt;
AuthorDate: Fri Nov 6 13:53:34 2015 -0800
Commit:     Justin Pettit &lt;jpettit@ovn.org&gt;
CommitDate: Fri Nov 6 16:33:29 2015 -0800

    TODO.md: Remove old item.
    
    The patchwork instance has been recreated, so this doesn't point any
    place valid.
    
    Signed-off-by: Justin Pettit &lt;jpettit@ovn.org&gt;
    Acked-by: Russell Bryant &lt;rbryant@redhat.com&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
