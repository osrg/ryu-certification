---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
cc3e1c99-c1cf-43c5-903f-29d767511f1d
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : bfc276a9-1307-495a-b8d2-fb592d0e8ae1
controller          : [e3a38f8a-98e7-4562-9067-ae0f2c16a0cf]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [115d29f7-9c15-4f22-a1ee-93fbee016603, 32f916cb-ac8a-4bba-a393-a2dec7f4ae7d, 681efd0f-91a3-4e55-9b06-db2ca9bb8905, f27f0a66-5856-43bc-bed6-4a8dc1baf97d]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e3a38f8a-98e7-4562-9067-ae0f2c16a0cf
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f27f0a66-5856-43bc-bed6-4a8dc1baf97d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f154ebd1-66b4-42af-af7b-32e8e4a7a573]
name                : "eth22"

_uuid               : 115d29f7-9c15-4f22-a1ee-93fbee016603
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [45b1b591-d0f0-492c-969f-5be9e3eee61b]
name                : "eth23"

_uuid               : 681efd0f-91a3-4e55-9b06-db2ca9bb8905
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [354cf75d-f4cc-493d-bb6b-dfe4e5516f2e]
name                : "br0"

_uuid               : 32f916cb-ac8a-4bba-a393-a2dec7f4ae7d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [847ada72-d876-4d10-82c0-32b330db9e2b]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 45b1b591-d0f0-492c-969f-5be9e3eee61b
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

_uuid               : f154ebd1-66b4-42af-af7b-32e8e4a7a573
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

_uuid               : 354cf75d-f4cc-493d-bb6b-dfe4e5516f2e
admin_state         : down
duplex              : full
ifindex             : 367
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

_uuid               : 847ada72-d876-4d10-82c0-32b330db9e2b
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 45f98d4cf831d795fe2a8f3e6a96b028b5617db6
Author:     Russell Bryant &lt;rbryant@redhat.com&gt;
AuthorDate: Tue Aug 18 11:26:21 2015 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Tue Aug 18 11:26:21 2015 -0700

    ovn: Free default db befor exit.
    
    The static result of default_db&#40;&#41; was malloc'd but not freed before
    exit.  Make the static result global and free it before exit.
    
    Signed-off-by: Russell Bryant &lt;rbryant@redhat.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
