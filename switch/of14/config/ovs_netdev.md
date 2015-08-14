---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
831a85cc-9d2d-4985-874b-cbb2e5ce7b2a
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
_uuid               : 88f7de79-d256-4f2f-8d29-71c9167cf101
controller          : [ecb74779-4a40-47e8-9f1a-f23df06c80fd]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [00b6809e-c653-4812-992c-117a652f7ca5, 3dfc8041-db7a-488e-ada4-5a4c5ea3d521, 75333a62-1af1-417a-ad06-b0b980c5a1f2, f912bce3-2a7d-4c1d-a14a-31a6fdb50020]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ecb74779-4a40-47e8-9f1a-f23df06c80fd
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3dfc8041-db7a-488e-ada4-5a4c5ea3d521
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [29237aa5-9c16-499b-880e-6e14d784fea2]
name                : "br0"

_uuid               : 00b6809e-c653-4812-992c-117a652f7ca5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [14966afc-23a5-433a-900e-b94108f793c0]
name                : "eth21"

_uuid               : 75333a62-1af1-417a-ad06-b0b980c5a1f2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [809c4d30-36f3-4be7-9f62-eb201776f297]
name                : "eth23"

_uuid               : f912bce3-2a7d-4c1d-a14a-31a6fdb50020
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2c146458-bc6b-4847-a1ee-137095338513]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2c146458-bc6b-4847-a1ee-137095338513
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

_uuid               : 14966afc-23a5-433a-900e-b94108f793c0
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

_uuid               : 809c4d30-36f3-4be7-9f62-eb201776f297
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

_uuid               : 29237aa5-9c16-499b-880e-6e14d784fea2
admin_state         : down
duplex              : full
ifindex             : 355
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
commit 600a8085e27f00a538e1abd14128606c67fcc7e1
Author:     Flavio Leitner &lt;fbl@redhat.com&gt;
AuthorDate: Thu Aug 13 16:06:29 2015 -0300
Commit:     Justin Pettit &lt;jpettit@nicira.com&gt;
CommitDate: Fri Aug 14 09:37:59 2015 -0700

    rhel: add installed but not packaged OVN tools
    
    This patch adds the following to OVN %files:
       /usr/bin/ovn-controller-vtep
       /usr/bin/ovn-sbctl
       /usr/share/man/man8/ovn-controller-vtep.8.gz
       /usr/share/man/man8/ovn-sbctl.8.gz
    
    Signed-off-by: Flavio Leitner &lt;fbl@redhat.com&gt;
    Signed-off-by: Justin Pettit &lt;jpettit@nicira.com&gt;
    Acked-by: Russell Bryant &lt;rbryant@redhat.com&gt;
</pre>
