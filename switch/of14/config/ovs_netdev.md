---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
cbae87bf-6a50-49d2-a31d-8dfb3596412a
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 38c367bb-91a2-4618-8be6-3ade27e9f852
controller          : [e6bb8fda-df0e-4efa-94d8-06cfb447bc60]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3b62e9d9-553c-4286-9a34-08c1d58a2cf6, be84e5bc-20e4-4d56-aee2-868149d31a90, c1aeab2d-8448-4ea1-a25d-0934e2ab7238, e543654e-6b36-42fd-83c4-b18f29ee97fa]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e6bb8fda-df0e-4efa-94d8-06cfb447bc60
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="647", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : be84e5bc-20e4-4d56-aee2-868149d31a90
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3c98df07-add0-4ea4-a32d-0de99e28ee13]
name                : "eth23"

_uuid               : c1aeab2d-8448-4ea1-a25d-0934e2ab7238
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7edf64d2-7519-4bc2-a725-42a48e860aae]
name                : "eth21"

_uuid               : 3b62e9d9-553c-4286-9a34-08c1d58a2cf6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fd215b89-efa8-4ccf-982b-f0f7204f953b]
name                : "eth22"

_uuid               : e543654e-6b36-42fd-83c4-b18f29ee97fa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bf7f70d7-b2e8-467d-a424-1a63a3652819]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : fd215b89-efa8-4ccf-982b-f0f7204f953b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9569823870, tx_dropped=0, tx_errors=0, tx_packets=6380943}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7edf64d2-7519-4bc2-a725-42a48e860aae
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
statistics          : {collisions=0, rx_bytes=11577502796, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=7721023, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 3c98df07-add0-4ea4-a32d-0de99e28ee13
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=221895000, tx_dropped=0, tx_errors=0, tx_packets=147930}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : bf7f70d7-b2e8-467d-a424-1a63a3652819
admin_state         : down
duplex              : full
ifindex             : 31
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
commit 88c98bf5635c732d4c77e5314ec7440a08a09dec
Author:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
AuthorDate: Wed May 6 19:00:26 2015 +0100
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu May 7 12:56:41 2015 -0700

    dpctl: Ignore enumeration errors if there is at least one datapath.
    
    When dpctl commands are used to inspect a userspace datapath, but OVS
    has also built-in support for the kernel datapath, an error message is
    reported if the kernel module is not loaded.  This commit suppresses the
    message.
    
    Suggested-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
