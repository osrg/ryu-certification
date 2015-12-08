---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b9a85ae6-2b59-4e21-af90-ed94bc066644
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : fad0811f-c0de-431f-9bde-3e908bb01e5a
controller          : [0d00694f-5743-48d3-aca1-04aa2cb0ff34]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [661f5cb2-74cc-459d-ab3c-13480e13cfff, a27537f2-784c-49ca-b96b-f926e2c1a7ff, bd0201b8-3978-4a8e-aca0-efe1387cab76, eaebe4fe-e3dd-46af-ad0a-98c0d815bd56]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0d00694f-5743-48d3-aca1-04aa2cb0ff34
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : bd0201b8-3978-4a8e-aca0-efe1387cab76
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c995899c-c232-4bc0-9ce1-bc473f78f20b]
name                : "br0"

_uuid               : a27537f2-784c-49ca-b96b-f926e2c1a7ff
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f8935175-f2fc-45a6-90f3-61c4deb00868]
name                : "eth22"

_uuid               : 661f5cb2-74cc-459d-ab3c-13480e13cfff
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [41b69817-400d-48cb-a9c5-2940cfec6633]
name                : "eth23"

_uuid               : eaebe4fe-e3dd-46af-ad0a-98c0d815bd56
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1eb9043c-9624-4612-8234-b793476fb854]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1eb9043c-9624-4612-8234-b793476fb854
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
statistics          : {collisions=0, rx_bytes=41810847155, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27920339, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c995899c-c232-4bc0-9ce1-bc473f78f20b
admin_state         : down
duplex              : full
ifindex             : 662
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

_uuid               : f8935175-f2fc-45a6-90f3-61c4deb00868
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29013896181, tx_dropped=0, tx_errors=0, tx_packets=19363219}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 41b69817-400d-48cb-a9c5-2940cfec6633
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6030318000, tx_dropped=0, tx_errors=0, tx_packets=4020212}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c883b4e804ee8cbb89a47e425bef76bd2bf6107b
Author:     Jarno Rajahalme &lt;jarno@ovn.org&gt;
AuthorDate: Tue Dec 8 11:35:49 2015 -0800
Commit:     Jarno Rajahalme &lt;jarno@ovn.org&gt;
CommitDate: Tue Dec 8 11:35:49 2015 -0800

    seq: Add a coverage counter for seq_change.
    
    Having a coverage counter tracking the value of the internal seq_next
    should help in debugging.
    
    Suggested-by: Justin Pettit &lt;jpettit@ovn.org&gt;
    Signed-off-by: Jarno Rajahalme &lt;jarno@ovn.org&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
