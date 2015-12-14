---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9d8a7e07-d395-4827-96df-68c86c63559f
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0034be47-3a0e-41b0-bad0-ab55e20bc260
controller          : [a686616b-b8bf-4f22-88a5-2333b8b9b4cb]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [865db9b0-e5c2-4524-a1fd-f4e80fdb773d, 9e7b51e8-0d5b-4afd-b180-f8e989b3ac00, a8586282-283e-42fc-8e20-260599ec80c7, c41ba7ae-7aae-46c7-a5a0-40ea1ba9d315]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a686616b-b8bf-4f22-88a5-2333b8b9b4cb
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9e7b51e8-0d5b-4afd-b180-f8e989b3ac00
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [47bbbb38-0b16-4eb3-867e-6f7c11a2fc0a]
name                : "eth22"

_uuid               : 865db9b0-e5c2-4524-a1fd-f4e80fdb773d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [db08274c-84eb-43ee-bb5e-e6d49693502f]
name                : "br0"

_uuid               : c41ba7ae-7aae-46c7-a5a0-40ea1ba9d315
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7555f35d-b124-42de-9086-44911bbf387b]
name                : "eth23"

_uuid               : a8586282-283e-42fc-8e20-260599ec80c7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6924a126-ae28-4127-9254-d6c8d90fb236]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 47bbbb38-0b16-4eb3-867e-6f7c11a2fc0a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29277460096, tx_dropped=0, tx_errors=0, tx_packets=19540532}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : db08274c-84eb-43ee-bb5e-e6d49693502f
admin_state         : down
duplex              : full
ifindex             : 682
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

_uuid               : 7555f35d-b124-42de-9086-44911bbf387b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6468639000, tx_dropped=0, tx_errors=0, tx_packets=4312426}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 6924a126-ae28-4127-9254-d6c8d90fb236
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
statistics          : {collisions=0, rx_bytes=42395936110, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28313687, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit eb1746e63583509510978eeb0df62a1c160dfdb3
Author:     Daniele Venturino &lt;daniele.venturino@m3s.it&gt;
AuthorDate: Fri Dec 11 13:59:00 2015 +0100
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Mon Dec 14 05:12:34 2015 -0800

    AUTHORS: Add Carlo Andreotti
    
    Carlo was involved in the testing and validation processes of the Rapid
    Spanning Tree Implementation.
    
    I also updated the Copyright string in some files.
    
    Signed-off by: Daniele Venturino &lt;daniele.venturino@m3s.it&gt;
    
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
