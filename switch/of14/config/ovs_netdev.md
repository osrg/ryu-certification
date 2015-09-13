---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1c8b47c6-3c61-4fc4-b6bd-4af0397e574b
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ec01949a-adc1-4686-850f-d8bb8ae8759a
controller          : [0eb612e7-ad26-4aa5-808b-f466c13d71f5]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1ba3c649-5f2e-4392-845b-300afd917634, 4362cad9-8df5-48df-9187-9b44f1ebdacb, 45f05048-e2b3-4687-a0bb-9840c2754e82, 899faf48-28ee-407a-9fce-841e9fdb3033]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0eb612e7-ad26-4aa5-808b-f466c13d71f5
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 45f05048-e2b3-4687-a0bb-9840c2754e82
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [547628b5-36c6-426b-ae4d-c13d31925a2d]
name                : "eth23"

_uuid               : 899faf48-28ee-407a-9fce-841e9fdb3033
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0a52ddaf-3503-4fa3-b195-e0561f4ad3f5]
name                : "eth21"

_uuid               : 1ba3c649-5f2e-4392-845b-300afd917634
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7be45f41-9e1e-4865-bfa0-bc34ebf2640b]
name                : "eth22"

_uuid               : 4362cad9-8df5-48df-9187-9b44f1ebdacb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [13965463-7b12-48e6-9bab-c654124e6936]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 547628b5-36c6-426b-ae4d-c13d31925a2d
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

_uuid               : 7be45f41-9e1e-4865-bfa0-bc34ebf2640b
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

_uuid               : 0a52ddaf-3503-4fa3-b195-e0561f4ad3f5
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

_uuid               : 13965463-7b12-48e6-9bab-c654124e6936
admin_state         : down
duplex              : full
ifindex             : 457
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
commit f41256d709d1733262b7538613237b34e801f457
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Fri Sep 11 09:01:05 2015 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Sun Sep 13 08:13:11 2015 -0700

    tunnel: Validate IP header for userspace tunneling.
    
    Currently, when doing userspace tunneling we don't perform much in
    the way of integrity checks on the incoming IP header. The case of
    tunneling is different from the usual case of switching since we are
    acting as the endpoint here and should not allow invalid packets to
    pass.
    
    This adds checks for IP checksum, version, total length, and options and
    drops packets that don't pass.
    
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
