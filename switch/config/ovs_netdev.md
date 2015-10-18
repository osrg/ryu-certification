---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
37c0ce22-3b1a-4bd9-9cdd-9babf2ea757a
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b417a1c3-d2f6-4ea6-aef3-adc27230cdbc
controller          : [8ce4fc3b-28c6-458f-8114-ac462a863c2a]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1f779e5b-ad3a-4984-a900-e5b90c74fdb4, 308599bd-b0bd-442c-bc16-3dbd826efee2, 6d739b32-3065-4a78-9abc-73ba48ff7cd3, 8d6ff73d-6827-4189-9a74-54a457d761c2]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8ce4fc3b-28c6-458f-8114-ac462a863c2a
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="757", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 308599bd-b0bd-442c-bc16-3dbd826efee2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [80e7303b-c415-41cb-b7e0-423aa9b5ecf7]
name                : "br0"

_uuid               : 8d6ff73d-6827-4189-9a74-54a457d761c2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [620e82be-b05b-46fc-8ba8-cbd43021ebaf]
name                : "eth21"

_uuid               : 6d739b32-3065-4a78-9abc-73ba48ff7cd3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1e3a1830-9c46-4671-bde1-4cb122ff6a36]
name                : "eth22"

_uuid               : 1f779e5b-ad3a-4984-a900-e5b90c74fdb4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1abf137a-afa9-459e-881c-243df95ce24d]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1e3a1830-9c46-4671-bde1-4cb122ff6a36
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=27507524044, tx_dropped=0, tx_errors=0, tx_packets=18350979}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 620e82be-b05b-46fc-8ba8-cbd43021ebaf
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
statistics          : {collisions=0, rx_bytes=38546046772, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=25725889, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1abf137a-afa9-459e-881c-243df95ce24d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3620169000, tx_dropped=0, tx_errors=0, tx_packets=2413446}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 80e7303b-c415-41cb-b7e0-423aa9b5ecf7
admin_state         : down
duplex              : full
ifindex             : 579
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a6755d50e5dc073cc15718bfeecd0fc8434972d2
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Sat Oct 17 14:03:53 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Sat Oct 17 14:45:17 2015 -0700

    packets: Make ip_parse_masked&#40;&#41; pickier about formatting.
    
    It's happened a couple of times now that I've entered a typoed IP address,
    e.g. &quot;192.168.0.0$x&quot;, and ip_parse_masked&#40;&#41; or its predecessor has accepted
    it anyway, and it's been hard to track down the real problem.  This change
    makes the parser pickier, by disallowing trailing garbage.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
