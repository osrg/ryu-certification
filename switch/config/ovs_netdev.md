---
layout: default
title: ovs_netdev - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b988ffa4-f35b-4dc0-ac97-62bd28372dd6
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth8"
            Interface "eth8"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth7"
            Interface "eth7"

$ sudo ovs-vsctl list Bridge
_uuid               : e5dab7dd-f8e6-47b4-a7cc-f63841d12567
controller          : [96763871-a28c-4015-be2e-4af6698cc14d]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [af168e06-dc50-4c1e-9e72-ec2dbb2c0de4, b758c903-044b-4eaa-badb-a51af675b082, d90a9f6e-fd32-4d08-8273-e5ff09e707fc]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 96763871-a28c-4015-be2e-4af6698cc14d
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="297", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : af168e06-dc50-4c1e-9e72-ec2dbb2c0de4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0518b775-95a4-4738-8583-f5ddd47e119a]
name                : "eth8"

_uuid               : d90a9f6e-fd32-4d08-8273-e5ff09e707fc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [db90b7f3-ce71-48bc-ad0f-964630085b03]
name                : "eth7"

_uuid               : b758c903-044b-4eaa-badb-a51af675b082
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1718dd55-f9fe-45e5-bfe3-6cb3efaec515]
name                : "br0"

$ sudo ovs-vsctl list Interface
_uuid               : 0518b775-95a4-4738-8583-f5ddd47e119a
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:ec"
mtu                 : 1550
name                : "eth8"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=328658, tx_dropped=0, tx_errors=0, tx_packets=3553}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 1718dd55-f9fe-45e5-bfe3-6cb3efaec515
admin_state         : up
duplex              : full
ifindex             : 63
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : db90b7f3-ce71-48bc-ad0f-964630085b03
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "eth7"
ofport              : 1
statistics          : {collisions=0, rx_bytes=875842, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=8969, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 758c456df570a1af1d9e913d50a3478785663e66
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Mon Dec 30 15:58:58 2013 -0800
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Mon Dec 30 16:52:43 2013 -0800

    dpif: Use explicit packet metadata.
    
    This helps reduce confusion about when a flow is a flow and when it is
    just metadata.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
