---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9c282900-b54b-4717-ad30-a956c1a3adfd
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 9fc9fa4d-bb83-482e-95f7-5480631a6784
controller          : [1e620239-458d-43c2-baa3-ac6acaaf891a]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0c2d4523-2204-4fae-b7d1-0649d6762182, 5502c26c-03ad-41dd-956a-e3382b54464a, 758bdd31-760e-49ca-b3ee-ac7986847ef8, e777c13f-ecb1-4d6a-b15a-0e028cc4d5e4]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 1e620239-458d-43c2-baa3-ac6acaaf891a
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=672, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5502c26c-03ad-41dd-956a-e3382b54464a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [70507b89-42f7-4f8b-a7a5-460ec29b31a1]
name                : br0

_uuid               : 758bdd31-760e-49ca-b3ee-ac7986847ef8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3d5d4ad6-908f-494e-be77-e09d2114fcd1]
name                : eth23

_uuid               : e777c13f-ecb1-4d6a-b15a-0e028cc4d5e4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8ac76d56-c6e7-40dc-8014-82757bf3da75]
name                : eth22

_uuid               : 0c2d4523-2204-4fae-b7d1-0649d6762182
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fbe8ea1a-f31d-40ff-ae85-b872392619d2]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 70507b89-42f7-4f8b-a7a5-460ec29b31a1
admin_state         : down
duplex              : full
ifindex             : 41
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : fbe8ea1a-f31d-40ff-ae85-b872392619d2
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=911718508, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=612400, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8ac76d56-c6e7-40dc-8014-82757bf3da75
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=371073552, tx_dropped=0, tx_errors=0, tx_packets=249528}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3d5d4ad6-908f-494e-be77-e09d2114fcd1
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=722889000, tx_dropped=0, tx_errors=0, tx_packets=481926}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 09e256031a62f8c3067563140d3f7cf30b0f1c85
Author:     Terry Wilson &lt;twilson@redhat.com&gt;
AuthorDate: Tue Aug 19 17:28:55 2014 -0600
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Aug 20 10:25:35 2014 -0700

    ovsdb: Allow comparison on optional scalar types
    
    This allows things like initiating a wait request on an interface
    ofport being set.
    
    When the optional field is empty and operation is != or excludes
    then the result is true; otherwise it is false. If the field is
    set then the field is compared normally for its type.
    
    Signed-off-by: Terry Wilson &lt;twilson@redhat.com&gt;
    [blp@nicira.com updated ovsdb-server&#40;1&#41; and NEWS.]
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
