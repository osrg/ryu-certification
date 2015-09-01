---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
eccea6ad-3ee2-4378-867b-4a87ace7bb8d
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 3ab05f4d-df60-4870-a1ab-eb87d309e5eb
controller          : [7bc3d7a1-d34a-4e5c-86fd-9761b442806e]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [37d73683-a717-416b-963f-8da4ae0c9295, 6ceee852-617a-4157-b486-d8ebc2650d81, 79baffe4-38d7-44f3-b41f-24fc5e22a5c2, 81e5e98d-1aef-47a8-92cd-44f65a9def78]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7bc3d7a1-d34a-4e5c-86fd-9761b442806e
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 79baffe4-38d7-44f3-b41f-24fc5e22a5c2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [038632fe-2ba9-436f-bbb3-1fb01c6d30da]
name                : "eth23"

_uuid               : 81e5e98d-1aef-47a8-92cd-44f65a9def78
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6d1ff2ee-9862-47e2-b65b-e16cd30d45bb]
name                : "eth22"

_uuid               : 6ceee852-617a-4157-b486-d8ebc2650d81
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dce08154-a246-48e8-86ac-5561b1a86374]
name                : "br0"

_uuid               : 37d73683-a717-416b-963f-8da4ae0c9295
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [69ba08d9-e0aa-4da6-b334-7ddef66679ae]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : dce08154-a246-48e8-86ac-5561b1a86374
admin_state         : down
duplex              : full
ifindex             : 415
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

_uuid               : 69ba08d9-e0aa-4da6-b334-7ddef66679ae
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

_uuid               : 6d1ff2ee-9862-47e2-b65b-e16cd30d45bb
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

_uuid               : 038632fe-2ba9-436f-bbb3-1fb01c6d30da
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 54b21db7235d51b75a45a477d57daa06cb9ffe55
Author:     Thadeu Lima de Souza Cascardo &lt;cascardo@redhat.com&gt;
AuthorDate: Tue Sep 1 17:56:09 2015 -0300
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Sep 1 13:59:30 2015 -0700

    ovs-ctl: Add option to delete transient ports.
    
    When using virtualization, new ports are created and removed all the time. These
    ports do not persist after a system reboot, for example. They may be created
    again by the virtualization manager, but that will happen after the vswitch is
    already running, and the virtualization manager will add them again to the
    bridge.
    
    If a reboot happens without properly deleting such ports, all kinds of errors
    will happen. The absence of the ports will be logged as errors, and adding those
    ports again to the database will fail.
    
    Deleting all bridges may not be an option, if the system cannot persist other
    information outside of OVSDB.
    
    This patch introduces the notion of transient ports. Ports may be added as
    transient, as a boolean in other_config smap. When openvswitch is started by
    using --delete-transient-ports ovs-ctl option, all transient ports will be
    removed.
    
    Signed-off-by: Thadeu Lima de Souza Cascardo &lt;cascardo@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
