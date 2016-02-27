---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
19511fe0-63b3-40c0-a87f-462c5942a941
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d5b4d9db-ab23-4536-bbbb-fc8bce5f44f4
controller          : [a6337490-84a6-4856-bef2-e2492417e01f]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [659275aa-05e6-49e6-8fb6-07c6ac814dbd, de1b4705-dc62-470c-b10a-8fdbd4679082, ed587829-ef58-4b2c-99f8-00a480645815, fbe1a8c2-29a9-47b3-81ad-e2b1e7578233]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a6337490-84a6-4856-bef2-e2492417e01f
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="12", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ed587829-ef58-4b2c-99f8-00a480645815
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [413b4980-887a-4c58-a3bc-d82eda6d3f3b]
name                : "eth22"

_uuid               : de1b4705-dc62-470c-b10a-8fdbd4679082
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [65626d06-1e38-4c30-9664-907fc2188acb]
name                : "eth21"

_uuid               : 659275aa-05e6-49e6-8fb6-07c6ac814dbd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [02385f4e-8095-4704-a5fd-454447e61ee4]
name                : "eth23"

_uuid               : fbe1a8c2-29a9-47b3-81ad-e2b1e7578233
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [517e13b9-74f9-4ec3-8e74-6133109169e9]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 413b4980-887a-4c58-a3bc-d82eda6d3f3b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31436431025, tx_dropped=0, tx_errors=0, tx_packets=20992988}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 517e13b9-74f9-4ec3-8e74-6133109169e9
admin_state         : down
duplex              : full
ifindex             : 840
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

_uuid               : 65626d06-1e38-4c30-9664-907fc2188acb
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
statistics          : {collisions=0, rx_bytes=47193639867, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31539115, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 02385f4e-8095-4704-a5fd-454447e61ee4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10065061500, tx_dropped=0, tx_errors=0, tx_packets=6710041}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7ae1f322d7794dc5c0528ef1a01154cbc58684d0
Author:     Ilya Maximets &lt;i.maximets@samsung.com&gt;
AuthorDate: Fri Feb 26 14:57:40 2016 +0300
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Fri Feb 26 16:55:08 2016 -0800

    testsuite: Add timeout to add_of_br&#40;&#41; command.
    
    Fixes hang of testsuite on ovs-vswitchd failure.
    
    Signed-off-by: Ilya Maximets &lt;i.maximets@samsung.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
