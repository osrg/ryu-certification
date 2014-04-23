---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4efb6053-c03c-4b77-b2fb-014568de9f67
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 330a9dac-f20f-485b-b99c-4fc76117a71f
controller          : [f202de33-5bdd-44f5-9af2-41b46ea2ef6f]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0edad11c-a23d-4162-89f7-b1bb76adb6d8, 7d77e086-098b-4d67-bd48-f18086a594f1, d9173217-7a60-48bb-8e22-668c5b919f51, e647e603-eba4-4efd-88c2-96f43a31bcf2]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f202de33-5bdd-44f5-9af2-41b46ea2ef6f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=567, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0edad11c-a23d-4162-89f7-b1bb76adb6d8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ae559f06-6ad1-4a8b-a6f6-022cdff4ef6d]
name                : br0

_uuid               : 7d77e086-098b-4d67-bd48-f18086a594f1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b7868a4e-1190-488b-8267-c0b36d04d9a5]
name                : eth21

_uuid               : e647e603-eba4-4efd-88c2-96f43a31bcf2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ca37fa53-652b-4f9a-b95b-a42efbddd408]
name                : eth22

_uuid               : d9173217-7a60-48bb-8e22-668c5b919f51
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [61ca706a-3d9b-42b6-82ec-6f1043397812]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 61ca706a-3d9b-42b6-82ec-6f1043397812
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1500
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=986779500, tx_dropped=0, tx_errors=0, tx_packets=657853}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ae559f06-6ad1-4a8b-a6f6-022cdff4ef6d
admin_state         : down
duplex              : full
ifindex             : 1103
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

_uuid               : b7868a4e-1190-488b-8267-c0b36d04d9a5
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=1995934381, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1343492, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ca37fa53-652b-4f9a-b95b-a42efbddd408
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1500
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1211283084, tx_dropped=0, tx_errors=0, tx_packets=812882}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 34799871bf18ce7d6124e137dcca31ef88af9156
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Wed Apr 23 14:06:12 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Apr 23 09:34:24 2014 -0700

    run-ryu: Use unix socket rather than patch ports
    
    My understanding of the implementation of patch ports is that they
    are rather special, being handled as a special case inside
    compose_output_action__&#40;&#41; and do not exist in the datapath.
    
    A side effect of the implementation of patch ports &#40;though perhaps not the
    portion mentioned above&#41; is that the OFPUTIL_PC_PORT_DOWN bit may not be
    set via a port mod message. In particular, the call to
    netdev_turn_flags_on&#40;&#41; in update_port_config&#40;&#41; fails.
    
    There is a test provided by Ryu that test this via port mod and thus fails.
    
    While that test could be modified or the results ignored it seems to me
    that it would be best if ryu-check used ports which were more fully
    featured and not special cases.
    
    Thus this patch moves run-ryu to use unix socket backed ports rather than
    patch ports.
    
    I believe a more significant problem with the use of patch ports
    is that they will require &#40;more&#41; special case code in order to correctly
    handle recirculation. As Ryu provides many tests that exercise
    recirculation for MPLS it would be nice if they could be used to exercise
    recirculation for MPLS &#40;which I have provided patches for separately[1]&#41;
    without the need to add more special-case code for that purpose.
    
    I believe that patch ports are also incompatible with recirculation for
    bonding, which has already been merged, though I have not verified that
    and it is not strictly related to this patch as I do not believe that Ryu
    provides any tests to exercise that case.
    
    The key problem with patch ports in the context of recirculation is that
    the ofproto and in_port may change during translation.  And this
    information is lost by the time that execution occurs.
    
    Furthermore the new in_port will not exist in the datapath as it is a
    patch port. That particular problem may be addressed by executing the
    actions in user-space, I have posted patches to provide infrastructure
    for that[1].
    
    Overall it is not clear to me that the complexity of supporting
    recirculation for patch-ports would have sufficient pay-off.
    
    [1] [PATCH v3 00/16] Flow-Based Recirculation for MPLS
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
