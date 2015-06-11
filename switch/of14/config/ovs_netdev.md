---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
13637087-330e-43c8-9601-f945adcd8a4a
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 931d65fb-70b3-494b-b6bb-66224091c098
controller          : [2e3e3b3f-cd2d-4e2f-8325-c7eb19a8fcee]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0ded1387-38b5-4010-bdc0-d162ed69504c, 380bcf0e-cb6b-4c3d-be14-b078c8e21ae8, 75a3abdb-1ab6-411c-9b02-85821c19df8e, 9972efa2-1009-419c-8008-8a8ae7ad6445]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2e3e3b3f-cd2d-4e2f-8325-c7eb19a8fcee
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9972efa2-1009-419c-8008-8a8ae7ad6445
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b45ddfe0-b788-4999-8e4a-1b1d10fc15e3]
name                : "eth23"

_uuid               : 380bcf0e-cb6b-4c3d-be14-b078c8e21ae8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b094a15b-ee7f-4bcc-a63c-0daa3855654d]
name                : "eth21"

_uuid               : 75a3abdb-1ab6-411c-9b02-85821c19df8e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8e7ca2db-c78f-4841-8136-285a8f8834ea]
name                : "eth22"

_uuid               : 0ded1387-38b5-4010-bdc0-d162ed69504c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [73fdd144-e90e-4323-88fc-8b7d22ee64b8]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 73fdd144-e90e-4323-88fc-8b7d22ee64b8
admin_state         : down
duplex              : full
ifindex             : 146
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

_uuid               : b45ddfe0-b788-4999-8e4a-1b1d10fc15e3
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

_uuid               : 8e7ca2db-c78f-4841-8136-285a8f8834ea
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

_uuid               : b094a15b-ee7f-4bcc-a63c-0daa3855654d
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 48954dab23eecfe895d7cb34c26587f400297618
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Tue Jun 9 10:29:43 2015 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Thu Jun 11 11:20:24 2015 -0700

    odp-util: Remove last use of odp_tun_key_from_attr for formatting.
    
    We formerly converted tunnel attributes to their flow representation
    before formatting but now perform all operations directly on the
    netlink attributes.
    
    There is one remaining use of odp_tun_key_from_attr&#40;&#41; that is not
    used for the purposes of generating a flow. This is to check the
    mask but this no longer makes sense given the way that we format
    the flow itself. In fact, the code is not actually invoked any
    more, so we can simply remove it.
    
    This retains the special case for tunnels as a safety measure but it
    should not matter in practice.
    
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
