---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4bfa384d-59e4-421f-a49f-3440911a144b
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ada1f18d-19a5-4675-bfa3-3295684edcfc
controller          : [f95b179f-9ba7-45f1-993a-34b08b0fe615]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4043a2c2-81d3-414d-a0a9-ea6a3ae14cc9, 946bcdd0-ddff-44a8-b186-bac2a8430d93, cf6bad8f-a7de-495d-bef1-2eb8170d0c29]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f95b179f-9ba7-45f1-993a-34b08b0fe615
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=372, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 946bcdd0-ddff-44a8-b186-bac2a8430d93
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b3ecd627-8a57-4281-82d2-7a4f2b4bece0]
name                : br0

_uuid               : 4043a2c2-81d3-414d-a0a9-ea6a3ae14cc9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [652414a8-956c-43c6-bd77-3d5d01986815]
name                : eth8

_uuid               : cf6bad8f-a7de-495d-bef1-2eb8170d0c29
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [037daee6-c880-4add-a1a1-31f360262f8d]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 652414a8-956c-43c6-bd77-3d5d01986815
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2535086, tx_dropped=0, tx_errors=0, tx_packets=27064}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 037daee6-c880-4add-a1a1-31f360262f8d
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=3059239947, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72594399, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : b3ecd627-8a57-4281-82d2-7a4f2b4bece0
admin_state         : up
duplex              : full
ifindex             : 310
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 53fd5c7c6d23f21872afcb041de1520fb9bb8343
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Feb 20 12:13:26 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Feb 20 12:13:26 2014 -0800

    ofproto: Update only OFPUTIL_PS_LINK_DOWN (not STP) from netdev state.
    
    When a netdev indicates that its state or configuration has changed,
    update_port() updates the OpenFlow port to match the changes.  However,
    this was being taken too far: a netdev does not have an STP state, and a
    state change was resetting the STP state of the port.  This fixes the
    problem.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Reported-by: Vasu Dasari &lt;vdasari@gmail.com&gt;
    Tested-by: Vasu Dasari &lt;vdasari@gmail.com&gt;
</pre>
