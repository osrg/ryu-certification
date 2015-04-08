---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
42ca56f8-7398-4b16-ae6c-c2b054355ade
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 1ed20f25-7b90-4294-bf22-f77e65d07fbb
controller          : [f465a91c-3af1-43ec-8313-27499cd0c1ae]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [27a5aa5f-bfdb-4800-a116-30f3c56eec20, a7108f9b-eefb-43f2-b584-7b3753b594ca, efa5128e-04bf-4ca1-b9b9-912483066311, f811eb8c-18d0-4593-b943-3015ca87b1b4]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f465a91c-3af1-43ec-8313-27499cd0c1ae
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="651", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f811eb8c-18d0-4593-b943-3015ca87b1b4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fd6bfa6e-47e9-4835-9a39-6d79a2fde37e]
name                : "eth21"

_uuid               : efa5128e-04bf-4ca1-b9b9-912483066311
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ece1a163-d242-46a8-8eb3-ebe355fbb304]
name                : "eth23"

_uuid               : 27a5aa5f-bfdb-4800-a116-30f3c56eec20
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0297fbf7-c700-4974-b5d8-c97e8f5bd84e]
name                : "eth22"

_uuid               : a7108f9b-eefb-43f2-b584-7b3753b594ca
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [68835d36-8b1c-44fe-b2bb-3afda0d4a08d]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : fd6bfa6e-47e9-4835-9a39-6d79a2fde37e
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
statistics          : {collisions=0, rx_bytes=1230556327411, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=820737412, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 68835d36-8b1c-44fe-b2bb-3afda0d4a08d
admin_state         : down
duplex              : full
ifindex             : 877
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

_uuid               : ece1a163-d242-46a8-8eb3-ebe355fbb304
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=40143312000, tx_dropped=0, tx_errors=0, tx_packets=26762208}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 0297fbf7-c700-4974-b5d8-c97e8f5bd84e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=629680302805, tx_dropped=0, tx_errors=0, tx_packets=419947976}
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
