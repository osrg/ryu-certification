---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9dfa1a37-ecfa-42c4-aff7-6b6643d1ba71
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 3b59173b-6cc8-446f-b348-1777958533af
controller          : [d1ef3a66-51d4-4051-9c41-c8e505ff340c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [a0b676bb-8f7c-4456-ab8e-15c6fee4e6c6, a54d9247-7774-4552-8cf5-29804f09268b, b417bda5-1e68-4108-abe8-f87318b767c0, c7de51ca-797b-4325-b786-76d1f5c5d624]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d1ef3a66-51d4-4051-9c41-c8e505ff340c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="747", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b417bda5-1e68-4108-abe8-f87318b767c0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9de92dd3-b683-4ddd-a735-54a6b52400b1]
name                : "eth23"

_uuid               : c7de51ca-797b-4325-b786-76d1f5c5d624
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [441b82a7-121a-4d08-bda5-e7de4a0f564d]
name                : "eth21"

_uuid               : a0b676bb-8f7c-4456-ab8e-15c6fee4e6c6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cd812ee0-167d-49bf-ac16-dab25305cbc4]
name                : "br0"

_uuid               : a54d9247-7774-4552-8cf5-29804f09268b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6377fdcc-95de-437c-9617-8dac0035eba5]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6377fdcc-95de-437c-9617-8dac0035eba5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=26980994764, tx_dropped=0, tx_errors=0, tx_packets=17997204}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : cd812ee0-167d-49bf-ac16-dab25305cbc4
admin_state         : down
duplex              : full
ifindex             : 559
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

_uuid               : 441b82a7-121a-4d08-bda5-e7de4a0f564d
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
statistics          : {collisions=0, rx_bytes=37375872882, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=24939337, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9de92dd3-b683-4ddd-a735-54a6b52400b1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2742937500, tx_dropped=0, tx_errors=0, tx_packets=1828625}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 848cb19882cccc90942e53d7d824d7ef23a4e7c5
Author:     Russell Bryant &lt;rbryant@redhat.com&gt;
AuthorDate: Tue Oct 13 09:44:53 2015 -0400
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Oct 13 09:27:14 2015 -0700

    ovn-tutorial: Add more links.
    
    Add links to several man pages.  Also fix a minor typo.
    
    Note that openvswitch.org needs to be updated as it's missing the
    ovn-northd man page.
    
    Signed-off-by: Russell Bryant &lt;rbryant@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
