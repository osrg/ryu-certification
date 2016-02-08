---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
cc00f2ea-3521-4fa4-bea0-09d1d0aee19a
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
_uuid               : 86bb683d-c94d-4f01-91e0-50a22f018338
controller          : [5c800ff5-b3a2-4a90-80a0-ce9fc2be3e15]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0dca718f-a091-4ea2-9ccb-7ade29028077, 0e9d7075-9940-4e30-bae5-ce9459a03065, 1ca57be0-3af9-4d97-9b28-ebcb9586cbdc, 4a58b802-b36c-4391-ae68-dd902055840d]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5c800ff5-b3a2-4a90-80a0-ce9fc2be3e15
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="16", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1ca57be0-3af9-4d97-9b28-ebcb9586cbdc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [16f4647a-bc10-449c-b504-7fe0a3190faa]
name                : "eth23"

_uuid               : 0e9d7075-9940-4e30-bae5-ce9459a03065
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bff77266-b47f-4f73-9c65-d8abf4692128]
name                : "eth22"

_uuid               : 4a58b802-b36c-4391-ae68-dd902055840d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ae26a063-a0af-4bb4-98ac-4c503a7a1166]
name                : "eth21"

_uuid               : 0dca718f-a091-4ea2-9ccb-7ade29028077
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1329647b-ab8d-49d7-b24f-47bd82da70dc]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 16f4647a-bc10-449c-b504-7fe0a3190faa
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=8661978000, tx_dropped=0, tx_errors=0, tx_packets=5774652}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : bff77266-b47f-4f73-9c65-d8abf4692128
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30593557155, tx_dropped=0, tx_errors=0, tx_packets=20425943}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1329647b-ab8d-49d7-b24f-47bd82da70dc
admin_state         : down
duplex              : full
ifindex             : 778
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

_uuid               : ae26a063-a0af-4bb4-98ac-4c503a7a1166
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
statistics          : {collisions=0, rx_bytes=45321410369, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30280441, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a7a5711094d30a263ddc223d5a8dde4313f62530
Author:     Ilya Maximets &lt;i.maximets@samsung.com&gt;
AuthorDate: Mon Feb 8 10:31:48 2016 +0300
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Mon Feb 8 08:30:00 2016 -0800

    manpages.mk: Remove ovs-benchmark.
    
    Fixes: e75291417990 &#40;&quot;ovs-benchmark: Remove.&quot;&#41;
    Signed-off-by: Ilya Maximets &lt;i.maximets@samsung.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
