---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ab45dddf-6ba9-4a14-ba5d-7a43e58b4da6
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 61cbd963-8760-4c45-8c6c-1ff16f5956e7
controller          : [ef6eac6a-993d-45c9-b6ba-c6a4a567b4c1]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [47886e20-bd8a-46a4-b0e6-2284a8a6d44c, 47f2a9eb-ce24-416b-b667-784d3d3f1128, 662b6623-e796-4669-9301-7f06f430e796, 6ac5aa09-0e98-404c-8d0b-31011899fa34]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ef6eac6a-993d-45c9-b6ba-c6a4a567b4c1
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="4", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 47886e20-bd8a-46a4-b0e6-2284a8a6d44c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [01233fd7-3b35-4f85-af9c-805c18c458ac]
name                : "eth23"

_uuid               : 6ac5aa09-0e98-404c-8d0b-31011899fa34
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [85c528a8-1f4a-47cd-aa52-ebe040a4b6d0]
name                : "eth21"

_uuid               : 662b6623-e796-4669-9301-7f06f430e796
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b565fc15-fdf3-45f1-81ca-c129e7a340fa]
name                : "br0"

_uuid               : 47f2a9eb-ce24-416b-b667-784d3d3f1128
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [44ba3073-2e54-4760-b7f6-158adf27c94f]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 85c528a8-1f4a-47cd-aa52-ebe040a4b6d0
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
statistics          : {collisions=0, rx_bytes=44268264092, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29572421, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b565fc15-fdf3-45f1-81ca-c129e7a340fa
admin_state         : down
duplex              : full
ifindex             : 740
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

_uuid               : 01233fd7-3b35-4f85-af9c-805c18c458ac
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7872423000, tx_dropped=0, tx_errors=0, tx_packets=5248282}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 44ba3073-2e54-4760-b7f6-158adf27c94f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30119743950, tx_dropped=0, tx_errors=0, tx_packets=20107178}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c5e8254adcb014a7fb487be4791eb074dd66ad37
Author:     Russell Bryant &lt;russell@ovn.org&gt;
AuthorDate: Wed Jan 27 15:10:08 2016 -0500
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Thu Jan 28 08:53:45 2016 -0500

    Add MAINTAINERS file.
    
    Previously, the list of committers was not written down publicly.  There
    was no reason for this other than it not being trivial to expose the
    commiter group membership via github.  This MAINTAINERS file lists the
    members of the OVS committers group.
    
    There's some outdated email addresses in here, but I just copied what
    was currently in AUTHORS.  This can be fixed when AUTHORS gets fixed,
    too.
    
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
