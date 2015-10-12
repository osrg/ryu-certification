---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0d736a76-4513-41f5-b7f2-60ad5be18f1b
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
_uuid               : cbb7284d-6939-449b-ba57-a2eaf14c5b07
controller          : [414b908e-9618-4e4a-889c-5413c248293f]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [552c8723-f6ae-4926-898d-eda85444e4bf, 5865cc4d-01fd-4b34-83dc-13c4b4852d83, b8066692-2849-4136-a4eb-21a1a1ba36f1, f93c2479-6bc1-4ab2-8fb8-49bf922c6500]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 414b908e-9618-4e4a-889c-5413c248293f
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="747", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f93c2479-6bc1-4ab2-8fb8-49bf922c6500
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [609c871d-88fe-42f4-82d0-8df5e289c2ba]
name                : "eth21"

_uuid               : 5865cc4d-01fd-4b34-83dc-13c4b4852d83
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [776769ca-f64b-431f-828b-4c0b6c340d8c]
name                : "br0"

_uuid               : b8066692-2849-4136-a4eb-21a1a1ba36f1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d525ecb3-5882-4b77-b423-24c3a3684add]
name                : "eth22"

_uuid               : 552c8723-f6ae-4926-898d-eda85444e4bf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1ca7d0cb-47ac-4514-a479-b0dfe6e1deab]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 609c871d-88fe-42f4-82d0-8df5e289c2ba
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
statistics          : {collisions=0, rx_bytes=37258846793, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=24860676, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 776769ca-f64b-431f-828b-4c0b6c340d8c
admin_state         : down
duplex              : full
ifindex             : 557
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

_uuid               : 1ca7d0cb-47ac-4514-a479-b0dfe6e1deab
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2655298500, tx_dropped=0, tx_errors=0, tx_packets=1770199}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d525ecb3-5882-4b77-b423-24c3a3684add
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=26928249586, tx_dropped=0, tx_errors=0, tx_packets=17961765}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e73e916510ce46af85fee4dd52127a699a244820
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Tue Sep 29 13:38:28 2015 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Mon Oct 12 11:34:51 2015 -0700

    rstp: Properly disable an RSTP port before deleting it.
    
    RSTP may end up referencing stale memory if a port is removed without
    disabling it first.
    
    This patch, together with the previous patch by Daniele Venturino, was
    tested to resolve a crach by Daniel Swahn.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Tested-by: Daniel Swahn &lt;daniel.swahn@clavister.com&gt;
</pre>
