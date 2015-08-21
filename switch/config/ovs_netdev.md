---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
956ce3cc-78f0-45b3-8578-2b4e7fdc99ee
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c832a8d3-a139-4622-bcb1-b2bed3aaed5b
controller          : [a13e0d70-a7cb-4654-8c3d-c0acf4706c0b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [4d07a979-3e9c-4f61-9c95-ce10d05490f6, 627df39a-e2e7-4279-bfd7-a0710db3d0eb, 65050e73-fa76-4874-9f1a-ef1f5ef11a28, e9c69a65-7109-4738-87af-b5a76b93ce27]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a13e0d70-a7cb-4654-8c3d-c0acf4706c0b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e9c69a65-7109-4738-87af-b5a76b93ce27
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [faa3b8ab-ea7c-42c4-9d23-0517d9e34a2e]
name                : "eth23"

_uuid               : 4d07a979-3e9c-4f61-9c95-ce10d05490f6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f299d4f0-eb92-4f7f-b5d1-98593ebf9eb7]
name                : "eth21"

_uuid               : 627df39a-e2e7-4279-bfd7-a0710db3d0eb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8bb0b1e3-2445-43d9-b677-192472bc6325]
name                : "eth22"

_uuid               : 65050e73-fa76-4874-9f1a-ef1f5ef11a28
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [87a8fe70-9074-4764-b39f-5766a7ec59b6]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 87a8fe70-9074-4764-b39f-5766a7ec59b6
admin_state         : down
duplex              : full
ifindex             : 375
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

_uuid               : f299d4f0-eb92-4f7f-b5d1-98593ebf9eb7
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

_uuid               : 8bb0b1e3-2445-43d9-b677-192472bc6325
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

_uuid               : faa3b8ab-ea7c-42c4-9d23-0517d9e34a2e
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
commit 24605d4e58ff5d74845d9ae9339f723c0f13608f
Author:     Simon Horman &lt;simon.horman@netronome.com&gt;
AuthorDate: Thu Aug 20 16:45:34 2015 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Fri Aug 21 11:03:02 2015 -0700

    ovs-ctl: do not attempt to restore flows when called with --delete-bridges
    
    When called with --delete-bridges saved flows cannot be restored as the
    bridges to which they belong no longer exist. This results in the following
    error messages on restart.
    
    ovs-ofctl: br0 is not a bridge or a socket
    Restoring saved flows ... failed!
    
    Although there is no effect of this error other than the message
    it seems worth avoiding. This patch does so by skipping saving of flows
    when --delete-bridges is in effect.
    
    As flows are no longer saved when --delete-bridges is in effect
    a side-effect of this change is that restart may be faster when
    there are many flows.
    
    Signed-off-by: Simon Horman &lt;simon.horman@netronome.com&gt;
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
