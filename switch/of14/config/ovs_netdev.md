---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2435c15d-a6fc-4b6e-87ae-7e8effb47bf6
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 6f9f9e88-1e7c-40fa-a2c8-a8c82d9f5968
controller          : [eecb5297-8b8a-479e-be35-5d207e2f4518]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [553e7298-7b9c-4804-a58c-8193de1c4324, 7efdfcb3-7ff6-49e6-9a0e-d59d5b165ae0, d2b06b49-82fd-4085-80f5-18e7f47ca1ad, e698d5a6-8f23-43d6-b145-2462306a57b0]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : eecb5297-8b8a-479e-be35-5d207e2f4518
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="16", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 553e7298-7b9c-4804-a58c-8193de1c4324
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [97619c5f-9c39-4c80-ba86-628464b17aad]
name                : "br0"

_uuid               : d2b06b49-82fd-4085-80f5-18e7f47ca1ad
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2e9d880b-70ec-4f5e-a2c3-ee5e63bbbcc1]
name                : "eth23"

_uuid               : e698d5a6-8f23-43d6-b145-2462306a57b0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b1dc9efd-df83-4e59-862b-501aecacafc1]
name                : "eth21"

_uuid               : 7efdfcb3-7ff6-49e6-9a0e-d59d5b165ae0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7301154a-0407-4c42-bbbb-4b4ea51c979e]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b1dc9efd-df83-4e59-862b-501aecacafc1
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
statistics          : {collisions=0, rx_bytes=44619316523, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29808432, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7301154a-0407-4c42-bbbb-4b4ea51c979e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30277704357, tx_dropped=0, tx_errors=0, tx_packets=20213450}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 2e9d880b-70ec-4f5e-a2c3-ee5e63bbbcc1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=8135586000, tx_dropped=0, tx_errors=0, tx_packets=5423724}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 97619c5f-9c39-4c80-ba86-628464b17aad
admin_state         : down
duplex              : full
ifindex             : 754
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
commit 8f169b874ea9e83827415bdf5b03bd9c17c743c5
Author:     Russell Bryant &lt;russell@ovn.org&gt;
AuthorDate: Mon Feb 1 09:58:22 2016 -0500
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Mon Feb 1 13:41:49 2016 -0500

    ovn-northd: Don't set custom log level defaults.
    
    ovn-northd set some custom log level defaults, which I believe were
    copied from ovs-vsctl.  Other daemons don't set this.  The difference in
    behavior in ovn-northd vs other daemons has caused some confusion during
    OpenStack+OVN development and testing, so make it consistent.
    
    Reported-by: Ryan Moats &lt;rmoats@us.ibm.com&gt;
    Reported-at: https://bugs.launchpad.net/bugs/1539994
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
    Acked-By: Kyle Mestery &lt;mestery@mestery.com&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
