---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4b6cb764-283a-4835-8bd0-e8aa3ccfaa11
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
_uuid               : e044ad56-74a7-4854-a9b1-7895f7da5d2b
controller          : [fd03a003-2b74-4a77-b7df-ca2ee4920b6a]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [4baabf45-37ba-4423-84ad-3a88802d362e, 4ee26d59-cb19-4fdb-97f8-7dcae1e287e0, bc750ee0-e9d3-4b37-a37f-9bd797aada66, d5b7924d-df8f-492f-aaee-53a420a05819]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : fd03a003-2b74-4a77-b7df-ca2ee4920b6a
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="752", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : bc750ee0-e9d3-4b37-a37f-9bd797aada66
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [070b685e-a06d-406f-a557-680d95af9988]
name                : "eth23"

_uuid               : d5b7924d-df8f-492f-aaee-53a420a05819
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [11c285f4-42ea-4ea1-92dd-065f210a8a01]
name                : "eth22"

_uuid               : 4ee26d59-cb19-4fdb-97f8-7dcae1e287e0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ab637f7b-9393-4584-9b44-ed46d4c4d8c7]
name                : "br0"

_uuid               : 4baabf45-37ba-4423-84ad-3a88802d362e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [705e4b27-a6ca-445e-8e35-bfd5ea67bf58]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 11c285f4-42ea-4ea1-92dd-065f210a8a01
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=26212828468, tx_dropped=0, tx_errors=0, tx_packets=17481301}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 070b685e-a06d-406f-a557-680d95af9988
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1560039000, tx_dropped=0, tx_errors=0, tx_packets=1040026}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 705e4b27-a6ca-445e-8e35-bfd5ea67bf58
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
statistics          : {collisions=0, rx_bytes=35749469141, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=23846294, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ab637f7b-9393-4584-9b44-ed46d4c4d8c7
admin_state         : down
duplex              : full
ifindex             : 532
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
commit 8c46162bb41c27c86523f59e6d0cbf91ea42b5d6
Author:     Jiri Benc &lt;jbenc@redhat.com&gt;
AuthorDate: Tue Sep 29 19:10:54 2015 -0300
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Oct 5 11:15:31 2015 -0700

    lib: Add ipv6 helper functions.
    
    ipv6_addr_is_set is going to be used by next patches.
    
    [cascardo: compare with in6addr_any in ipv6_addr_is_set]
    [cascardo: keep only ipv6_addr_is_* functions]
    
    Signed-off-by: Jiri Benc &lt;jbenc@redhat.com&gt;
    Signed-off-by: Thadeu Lima de Souza Cascardo &lt;cascardo@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
