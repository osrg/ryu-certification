---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1f7c7363-4739-434d-981e-92bfa2a54b78
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 5c5253bf-4db9-4490-9df4-0ce250c1fd56
controller          : [8b43af7c-6969-4b0d-b7f0-cc3305386e4d]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2218fb7e-a9c0-487b-9f71-26f34bc30dd4, 2e1ade04-ff62-444e-9888-27f5c502f81b, 5442b3f8-465d-450d-ad3e-cd966eed5569, 62bdcc76-70ba-446e-af2d-02ec900ba3e8]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8b43af7c-6969-4b0d-b7f0-cc3305386e4d
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5442b3f8-465d-450d-ad3e-cd966eed5569
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4404c826-ce53-4a85-ae32-536e417846fe]
name                : "br0"

_uuid               : 2e1ade04-ff62-444e-9888-27f5c502f81b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dc595c82-49f2-4c6b-8038-1477339d11f2]
name                : "eth23"

_uuid               : 62bdcc76-70ba-446e-af2d-02ec900ba3e8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [47ed0b39-17e5-4601-ad77-323aa750085f]
name                : "eth21"

_uuid               : 2218fb7e-a9c0-487b-9f71-26f34bc30dd4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [922a158d-bce9-4e2a-b8e4-31bdcc7c6fee]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 922a158d-bce9-4e2a-b8e4-31bdcc7c6fee
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28855904274, tx_dropped=0, tx_errors=0, tx_packets=19256926}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 47ed0b39-17e5-4601-ad77-323aa750085f
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
statistics          : {collisions=0, rx_bytes=41459790224, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27684325, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 4404c826-ce53-4a85-ae32-536e417846fe
admin_state         : down
duplex              : full
ifindex             : 648
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

_uuid               : dc595c82-49f2-4c6b-8038-1477339d11f2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5767173000, tx_dropped=0, tx_errors=0, tx_packets=3844782}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 578b73e89b59430c990ff175146a06b47bcd3e0a
Author:     Ben Pfaff &lt;blp@ovn.org&gt;
AuthorDate: Thu Dec 3 23:00:32 2015 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Fri Dec 4 09:01:51 2015 -0800

    ovs-ofctl: Fix manpage formatting typo.
    
    Only the names of the fields were supposed to be bold here, but omitting
    the &quot;fR&quot; from &quot;\fR&quot; made everything between the field names bold too,
    which looked funny.
    
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
    Acked-by: Justin Pettit &lt;jpettit@ovn.org&gt;
</pre>
