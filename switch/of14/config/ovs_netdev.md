---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3801edf1-5354-4fab-8f29-843dba586a28
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7a16bd33-7bd1-4ae3-aada-7fd12b30b575
controller          : [360369c8-03d9-4115-bfd3-1ba11b1e2014]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [617a7e05-3247-4b28-821f-7787e415f558, 806a16d1-9a4c-41ca-8636-92eb39dee0c1, 9fa33c34-4e67-42ba-b9a0-4c942a7bfd93, dfc6f5d7-e67d-44c7-90c9-9c3372b1c307]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 360369c8-03d9-4115-bfd3-1ba11b1e2014
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9fa33c34-4e67-42ba-b9a0-4c942a7bfd93
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [40b59bfb-36e6-423f-8863-bad7030b7f71]
name                : "eth21"

_uuid               : 806a16d1-9a4c-41ca-8636-92eb39dee0c1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [19ce30fb-5552-4017-b383-4766bc9fc9fe]
name                : "eth23"

_uuid               : 617a7e05-3247-4b28-821f-7787e415f558
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0f8b6980-ffce-483e-bfff-9dea8a98e430]
name                : "eth22"

_uuid               : dfc6f5d7-e67d-44c7-90c9-9c3372b1c307
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3bf737e9-0bb6-4c9e-a898-11f2f8eb5e74]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0f8b6980-ffce-483e-bfff-9dea8a98e430
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

_uuid               : 3bf737e9-0bb6-4c9e-a898-11f2f8eb5e74
admin_state         : down
duplex              : full
ifindex             : 88
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

_uuid               : 40b59bfb-36e6-423f-8863-bad7030b7f71
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

_uuid               : 19ce30fb-5552-4017-b383-4766bc9fc9fe
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
