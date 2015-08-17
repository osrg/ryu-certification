---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
114bb39e-34dd-4d16-ac07-c0d71985c20e
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 76de0fa7-7e78-4847-87bc-92fae9ea25d2
controller          : [a4cd8372-b7b9-4965-8309-701589391a1f]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [8bae066b-584e-4f75-a1be-d9c588911b6e, 8f06a48e-f74e-43ae-bebf-cc89f49ff913, b011f065-d3c4-47f0-91da-790ebb5b6bf5, da21c8f5-270e-46dc-b039-c597f74f036f]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a4cd8372-b7b9-4965-8309-701589391a1f
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b011f065-d3c4-47f0-91da-790ebb5b6bf5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d97ad267-0523-4df1-9795-1a69e0d0bcc8]
name                : "eth22"

_uuid               : da21c8f5-270e-46dc-b039-c597f74f036f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [101fd28f-d9b1-4c7a-a539-90cd6057cf4c]
name                : "eth21"

_uuid               : 8f06a48e-f74e-43ae-bebf-cc89f49ff913
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [154cfc4d-d88e-4f3d-95bc-ec21c263231a]
name                : "eth23"

_uuid               : 8bae066b-584e-4f75-a1be-d9c588911b6e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [766b5930-c3d3-403a-9295-cee0fa8f7bf2]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 766b5930-c3d3-403a-9295-cee0fa8f7bf2
admin_state         : down
duplex              : full
ifindex             : 359
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

_uuid               : 154cfc4d-d88e-4f3d-95bc-ec21c263231a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1176922500, tx_dropped=0, tx_errors=0, tx_packets=784615}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 101fd28f-d9b1-4c7a-a539-90cd6057cf4c
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
statistics          : {collisions=0, rx_bytes=24024581534, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16026376, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d97ad267-0523-4df1-9795-1a69e0d0bcc8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18089315792, tx_dropped=0, tx_errors=0, tx_packets=12064077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6228d33fee706314ea1e3e1d3a76eada5ad5a3d1
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Fri Jul 3 22:55:24 2015 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Sun Aug 16 17:08:37 2015 -0700

    ovn-controller-vtep: Add binding module.
    
    This commit adds the binding module to ovn-controller-vtep.  The
    module will scan through the Port_Binding table in ovnsb.  If there is
    a port binding entry for a logical switch on the vtep gateway chassis's
    &quot;vtep_logical_switches&quot;, sets the port binding's chassis column to the
    vtep gateway chassis.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Russell Bryant &lt;rbryant@redhat.com&gt;
</pre>
