---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fcb423a3-c745-4b69-9493-81c3bedbd33e
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
_uuid               : 4e26678b-d5bc-4848-950c-ede79769abfc
controller          : [eb324882-26e3-49b0-9409-41571891a673]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [5094d86f-8206-4661-97c7-104abd1d9b7d, 8935fa5a-f90c-4f7b-ad3c-84908097c837, c06286e6-75da-4c69-a61c-340840638c9a, da69a74b-45b9-41c8-863a-856c977e8431]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : eb324882-26e3-49b0-9409-41571891a673
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c06286e6-75da-4c69-a61c-340840638c9a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [307b3692-2cab-48c9-a522-eb06c3bead87]
name                : "br0"

_uuid               : 8935fa5a-f90c-4f7b-ad3c-84908097c837
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7c60e9e7-a467-4cd6-bc3f-971b17fde775]
name                : "eth23"

_uuid               : 5094d86f-8206-4661-97c7-104abd1d9b7d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7b1bb2a1-e624-4d31-bf21-585afb55d735]
name                : "eth22"

_uuid               : da69a74b-45b9-41c8-863a-856c977e8431
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [004af12b-aee6-491a-81fd-f79fa647770d]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7b1bb2a1-e624-4d31-bf21-585afb55d735
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

_uuid               : 307b3692-2cab-48c9-a522-eb06c3bead87
admin_state         : down
duplex              : full
ifindex             : 86
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

_uuid               : 004af12b-aee6-491a-81fd-f79fa647770d
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

_uuid               : 7c60e9e7-a467-4cd6-bc3f-971b17fde775
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
commit c05c01cd86bdb26be1c107741c3ede2659e51a29
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Fri May 29 10:41:05 2015 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Fri May 29 10:52:57 2015 -0700

    odp-util: Fix alignment when scanning Geneve attributes.
    
    Clang complains about the fact that we use a byte array to scan
    Geneve attributes into since there are different alignment requirements:
    
    lib/odp-util.c:2936:30: error: cast from 'uint8_t *' &#40;aka 'unsigned char *'&#41; to
    
          'struct geneve_opt *' increases required alignment from 1 to 2
    
          [-Werror,-Wcast-align]
    
        struct geneve_opt *opt = &#40;struct geneve_opt *&#41;key-&gt;d;
    
                                 ^~~~~~~~~~~~~~~~~~~~~~~~~~~
    
    We can instead treat this as an array of Geneve option headers to
    ensure we get the right alignment and then there are no need for
    casts.
    
    Reported-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
