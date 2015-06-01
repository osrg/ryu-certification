---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f7c08e9e-79e7-4fb8-97f9-4579482caca8
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 690aaea7-7f8d-471a-898a-224986602440
controller          : [27e67bc0-6691-4a4b-aa83-792d7d7d0070]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [ed65ee56-5842-4ad2-bed0-2536c3196e78, f4eb3879-e68b-4787-a862-5399135cc229, f5feeb94-b0d0-474e-bd62-b7fbc7959e99, fc9f52ad-3902-48f6-b945-385c04aeac2b]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 27e67bc0-6691-4a4b-aa83-792d7d7d0070
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f5feeb94-b0d0-474e-bd62-b7fbc7959e99
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f7857975-3305-4951-9091-b4a6ff074957]
name                : "eth23"

_uuid               : f4eb3879-e68b-4787-a862-5399135cc229
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9cfa6444-5c1c-483c-b43e-0b6bcb169767]
name                : "eth22"

_uuid               : fc9f52ad-3902-48f6-b945-385c04aeac2b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a96e6873-d81e-4125-84d0-2879eda6ff32]
name                : "br0"

_uuid               : ed65ee56-5842-4ad2-bed0-2536c3196e78
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6ba295eb-132f-4034-b2e0-9b181c95d0e0]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9cfa6444-5c1c-483c-b43e-0b6bcb169767
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

_uuid               : f7857975-3305-4951-9091-b4a6ff074957
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

_uuid               : a96e6873-d81e-4125-84d0-2879eda6ff32
admin_state         : down
duplex              : full
ifindex             : 94
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

_uuid               : 6ba295eb-132f-4034-b2e0-9b181c95d0e0
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
commit 186120da7fc0f20d93778623a006c152f7cd5e90
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Fri May 29 11:28:38 2015 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Mon Jun 1 13:25:11 2015 -0700

    classifier: Support duplicate rules.
    
    OpenFlow 1.4 bundles are easier to implement when it is possible to
    mark a rule as 'to_be_removed' and then insert a new, identical rule
    with the same priority.
    
    All but one out of the identical rules must be marked as
    'to_be_removed', and the one rule that is not 'to_be_removed' must
    have been inserted last.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
