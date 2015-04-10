---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
62b2ddbc-2a3e-4314-9219-6f6883bfe2fe
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
_uuid               : af5854f6-24c7-4238-8691-5a1d8e49a470
controller          : [f111ab0f-6113-4abf-8a96-b6e42034df4c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2cd3f689-4390-4dfb-a11e-ac2e95c181ad, 6869b2a4-d9a2-4aa4-983d-c5d2ed53bd08, 7ba40f8f-6054-417c-8048-f9ffb4b2c2cc, ad32e3b6-2ed6-4b16-a864-b224e6fc4740]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f111ab0f-6113-4abf-8a96-b6e42034df4c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="657", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6869b2a4-d9a2-4aa4-983d-c5d2ed53bd08
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c9404642-5775-488d-8bf2-fd7dec2beaa4]
name                : "eth22"

_uuid               : 2cd3f689-4390-4dfb-a11e-ac2e95c181ad
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1850ae46-3187-44e7-9604-83ae8b3ccc66]
name                : "eth23"

_uuid               : ad32e3b6-2ed6-4b16-a864-b224e6fc4740
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [19ef40bc-3840-4873-b073-a82993b49c16]
name                : "eth21"

_uuid               : 7ba40f8f-6054-417c-8048-f9ffb4b2c2cc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b91dddb9-216e-46e6-b2c3-8879fd6df478]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 19ef40bc-3840-4873-b073-a82993b49c16
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
statistics          : {collisions=0, rx_bytes=1230907124386, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=820973204, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b91dddb9-216e-46e6-b2c3-8879fd6df478
admin_state         : down
duplex              : full
ifindex             : 883
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

_uuid               : c9404642-5775-488d-8bf2-fd7dec2beaa4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=629838043636, tx_dropped=0, tx_errors=0, tx_packets=420054049}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1850ae46-3187-44e7-9604-83ae8b3ccc66
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=40406457000, tx_dropped=0, tx_errors=0, tx_packets=26937638}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e8fe6ad03aa3d25b5ae99190d5aa065705a1b3c8
Author:     Flavio Leitner &lt;fbl@redhat.com&gt;
AuthorDate: Fri Apr 10 11:08:10 2015 -0300
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Fri Apr 10 08:54:41 2015 -0700

    tests: gre: fix flags endianness
    
    The flags field is 16 bits so use network byte order in the
    test case and use the proper conversion methods when parsing
    and dumping.
    
    Signed-off-by: Flavio Leitner &lt;fbl@redhat.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
