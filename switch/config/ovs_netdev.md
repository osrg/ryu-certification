---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
efb3711a-4280-44ab-85bd-6fffd978047a
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b7e1f458-0e51-49ad-9b0f-223525c98ede
controller          : [cbeb3c90-b17c-45ce-bb7c-5c0c0ec963f7]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1f990256-dd70-4911-b52b-60cae8e3d851, 5e3dc458-e485-48a6-889c-d0469ff20b87, 88043922-2000-441a-8c39-15c0c39979e3]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : cbeb3c90-b17c-45ce-bb7c-5c0c0ec963f7
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=371, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5e3dc458-e485-48a6-889c-d0469ff20b87
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [07b4e2d2-2dd5-4853-b986-fadd293adc0b]
name                : eth7

_uuid               : 88043922-2000-441a-8c39-15c0c39979e3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [de758bb8-1509-4ea5-ae15-de268ca80340]
name                : br0

_uuid               : 1f990256-dd70-4911-b52b-60cae8e3d851
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0cbdf5c4-4fee-4335-bb9b-7a5732bba180]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0cbdf5c4-4fee-4335-bb9b-7a5732bba180
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3956484, tx_dropped=0, tx_errors=0, tx_packets=42204}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : de758bb8-1509-4ea5-ae15-de268ca80340
admin_state         : up
duplex              : full
ifindex             : 533
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

_uuid               : 07b4e2d2-2dd5-4853-b986-fadd293adc0b
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
statistics          : {collisions=0, rx_bytes=3064108234, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72643835, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0d1cee123a84ef8885834c0d086c4a3d5d48355f
Author:     kmindg &lt;kmindg@gmail.com&gt;
AuthorDate: Sun Mar 9 17:48:52 2014 +0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Sat Mar 15 09:39:11 2014 -0700

    stp: Fix bpdu tx problem in listening state
    
    The restriction only allows to send bpdu in forwarding state in
    compose_output_action__. But a port could send bpdu in listening
    and learning state according to comments in lib/stp.h(State of
    an STP port).
    
    Until this commit, OVS did not send out BPDUs in listening and learning
    states.  But those two states are temporary, the stp port will be in
    forwarding state and send out BPDUs eventually (In the default
    configuration listening and learning states last 15+15 second).  Therefore,
    this bug increased convergence time but did not entirely break STP.
    
    Signed-off-by: kmindg &lt;kmindg@gmail.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
