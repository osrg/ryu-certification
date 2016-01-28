---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a6799895-fe1f-46f6-8ba2-36192be338b2
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
_uuid               : 9f45d6d5-4ce5-4218-9c6d-028b4f8582e2
controller          : [4d6fbce2-ffec-4527-ae17-5e121e8cb5eb]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1af579cd-f1d8-47a1-bf7c-9c7667f251f8, 30165459-ddd3-4fd8-a1b5-60244990fa64, 690ede6d-af98-4357-9316-545e3cc9167b, eb88dd6a-d6c0-4f9f-90d9-24da6331a9e7]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4d6fbce2-ffec-4527-ae17-5e121e8cb5eb
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 30165459-ddd3-4fd8-a1b5-60244990fa64
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b0651180-80a7-44f3-aab8-1a1fbdef0cc0]
name                : "eth22"

_uuid               : 1af579cd-f1d8-47a1-bf7c-9c7667f251f8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7c1812d5-3d2c-45f0-bd83-fb75d06919ec]
name                : "eth21"

_uuid               : 690ede6d-af98-4357-9316-545e3cc9167b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [24363167-76bc-4d23-ac3e-c8a5ad33d7f7]
name                : "eth23"

_uuid               : eb88dd6a-d6c0-4f9f-90d9-24da6331a9e7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e98386de-606c-4de5-abee-034579a847b3]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b0651180-80a7-44f3-aab8-1a1fbdef0cc0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30119744208, tx_dropped=0, tx_errors=0, tx_packets=20107181}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7c1812d5-3d2c-45f0-bd83-fb75d06919ec
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
statistics          : {collisions=0, rx_bytes=44268264350, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29572424, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : e98386de-606c-4de5-abee-034579a847b3
admin_state         : down
duplex              : full
ifindex             : 742
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

_uuid               : 24363167-76bc-4d23-ac3e-c8a5ad33d7f7
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
