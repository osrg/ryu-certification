---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fa3b9c2e-d073-42ce-b301-8ef202493b05
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b0d47478-9b6d-43ac-b83c-00e282605758
controller          : [4edbfd2d-0d6c-4efa-aa9c-899d61f7b20b]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [498ad535-3a15-42c7-be1a-1e39523df438, 599fb873-7c67-4a58-913f-e4b583b68a10, be8794b6-866c-4cac-9c50-25f1c4dbe1b4]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4edbfd2d-0d6c-4efa-aa9c-899d61f7b20b
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=372, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 498ad535-3a15-42c7-be1a-1e39523df438
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d0381f01-8109-4b5d-aa64-8300592e6d5e]
name                : eth7

_uuid               : be8794b6-866c-4cac-9c50-25f1c4dbe1b4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d73409a3-727b-4773-904f-6a3c2a02c227]
name                : eth8

_uuid               : 599fb873-7c67-4a58-913f-e4b583b68a10
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a3e52aed-36db-49ef-b172-b2ab0b23ea32]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a3e52aed-36db-49ef-b172-b2ab0b23ea32
admin_state         : up
duplex              : full
ifindex             : 306
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

_uuid               : d0381f01-8109-4b5d-aa64-8300592e6d5e
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
statistics          : {collisions=0, rx_bytes=3059158757, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72593573, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : d73409a3-727b-4773-904f-6a3c2a02c227
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2511820, tx_dropped=0, tx_errors=0, tx_packets=26816}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
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
