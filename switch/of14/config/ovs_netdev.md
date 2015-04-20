---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fe78a9aa-bb94-4619-90a6-e2f301df0fad
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f7df6b3b-79a4-42a1-9b17-b54de324da32
controller          : [27d5f748-e88c-49b3-b45a-b52fda887f7c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [5ccb3f53-5573-4bfc-9d46-b7066ca03eaa, b7c1bbd9-dab3-4a80-a252-f61a006c99c3, c734bd8b-9614-420f-98b8-09813232cfe5, e8668995-a7d3-46ec-836b-dd88c65a9ab4]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 27d5f748-e88c-49b3-b45a-b52fda887f7c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="652", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e8668995-a7d3-46ec-836b-dd88c65a9ab4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2a285354-8114-4ea8-95f4-45526b96bb7a]
name                : "eth23"

_uuid               : b7c1bbd9-dab3-4a80-a252-f61a006c99c3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e1905718-0948-4f26-82ae-39e8c2f0da44]
name                : "eth21"

_uuid               : c734bd8b-9614-420f-98b8-09813232cfe5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6ec80890-70b9-4c56-b117-eccc937c502d]
name                : "br0"

_uuid               : 5ccb3f53-5573-4bfc-9d46-b7066ca03eaa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c2eacc9d-4ff9-432a-9fc9-7c74a8af0ea7]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e1905718-0948-4f26-82ae-39e8c2f0da44
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
statistics          : {collisions=0, rx_bytes=1233362245711, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=822623443, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 2a285354-8114-4ea8-95f4-45526b96bb7a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=42248407500, tx_dropped=0, tx_errors=0, tx_packets=28165605}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 6ec80890-70b9-4c56-b117-eccc937c502d
admin_state         : down
duplex              : full
ifindex             : 925
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

_uuid               : c2eacc9d-4ff9-432a-9fc9-7c74a8af0ea7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=630941866453, tx_dropped=0, tx_errors=0, tx_packets=420796318}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 28e2fa027d8c44f0970e3f2f12911f8c1cdde3a2
Author:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
AuthorDate: Wed Apr 15 19:11:49 2015 +0100
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Mon Apr 20 12:56:29 2015 -0700

    dpif-netdev: Batch packets when recirculating.
    
    Now that we have per packet metadata, there's no need to split packet
    batches when recirculating.
    
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
