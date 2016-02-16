---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
eeee391a-a2dc-43c8-8979-0a789f8a2f59
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 54c776b2-37e1-4489-999b-23eb55f27110
controller          : [47b05c6d-62f1-490a-a792-12d3d6dd9f01]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3710e8c7-04af-4496-bd11-7f9705128a21, 74794224-0b91-4311-a3ad-b3ac3b2d5127, d88a3f3b-45dd-4b95-a58f-024b8e70a6a2, e4671f7f-0a9a-4896-a9ef-61c47286930f]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 47b05c6d-62f1-490a-a792-12d3d6dd9f01
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 74794224-0b91-4311-a3ad-b3ac3b2d5127
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ea983aa8-eaef-4674-9204-0c5d01f53bb9]
name                : "eth22"

_uuid               : d88a3f3b-45dd-4b95-a58f-024b8e70a6a2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c4b157c1-ead3-42f1-93b9-17ead1824fb8]
name                : "eth23"

_uuid               : e4671f7f-0a9a-4896-a9ef-61c47286930f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b260226c-851d-41ab-beeb-140d5c9df7bb]
name                : "br0"

_uuid               : 3710e8c7-04af-4496-bd11-7f9705128a21
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [92d74252-5d75-4a67-8de6-8a21f08ef67f]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b260226c-851d-41ab-beeb-140d5c9df7bb
admin_state         : down
duplex              : full
ifindex             : 798
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

_uuid               : ea983aa8-eaef-4674-9204-0c5d01f53bb9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30909679437, tx_dropped=0, tx_errors=0, tx_packets=20638610}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c4b157c1-ead3-42f1-93b9-17ead1824fb8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9188097000, tx_dropped=0, tx_errors=0, tx_packets=6125398}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 92d74252-5d75-4a67-8de6-8a21f08ef67f
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
statistics          : {collisions=0, rx_bytes=46023497699, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30752440, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7c6401ca2b8c718e274a89928c4b602a1904342a
Author:     Thadeu Lima de Souza Cascardo &lt;cascardo@redhat.com&gt;
AuthorDate: Mon Feb 15 15:14:21 2016 -0200
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Tue Feb 16 09:34:38 2016 -0800

    netdev-linux: Fix warning message.
    
    Instead of reading
    
    &quot;error receiving Ethernet packet on Permission denied: ens3&quot;,
    
    it should read
    
    &quot;error receiving Ethernet packet on ens3: Permission denied&quot;.
    
    Signed-off-by: Thadeu Lima de Souza Cascardo &lt;cascardo@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
