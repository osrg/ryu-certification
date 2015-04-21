---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1c533581-d4bb-4438-949e-7f9ba348fa23
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 96e8ce91-eb76-46ee-aefa-78a5abd06f39
controller          : [ca3135be-da86-42a8-9724-ddbf676f3015]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0c38b0d8-145e-4bf4-8c06-e310376db182, 4abc667b-8449-4a62-bf52-30cf7885a2ee, 5d4c0b5f-d6d2-4b8a-b7cb-cc648c97bcb6, ebc3da49-4c1e-48af-a5b5-2cac1c2b8fd4]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ca3135be-da86-42a8-9724-ddbf676f3015
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="657", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0c38b0d8-145e-4bf4-8c06-e310376db182
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [be8eedc2-1498-4038-9979-eb5ea917127e]
name                : "eth21"

_uuid               : ebc3da49-4c1e-48af-a5b5-2cac1c2b8fd4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [37a620a4-ab2c-4824-98eb-f7fb3c7683a4]
name                : "br0"

_uuid               : 5d4c0b5f-d6d2-4b8a-b7cb-cc648c97bcb6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2b3706da-298c-41df-8de3-9e1f1ae6c09f]
name                : "eth22"

_uuid               : 4abc667b-8449-4a62-bf52-30cf7885a2ee
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [beff9cea-444d-42c8-9831-025f2728e728]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 37a620a4-ab2c-4824-98eb-f7fb3c7683a4
admin_state         : down
duplex              : full
ifindex             : 927
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

_uuid               : beff9cea-444d-42c8-9831-025f2728e728
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=42335860500, tx_dropped=0, tx_errors=0, tx_packets=28223907}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 2b3706da-298c-41df-8de3-9e1f1ae6c09f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=630994691730, tx_dropped=0, tx_errors=0, tx_packets=420831839}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : be8eedc2-1498-4038-9979-eb5ea917127e
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
statistics          : {collisions=0, rx_bytes=1233479158036, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=822702027, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 186de41979352a7f111e3eec6744778d80ac17b0
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Mon Apr 20 12:11:23 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Apr 21 08:29:30 2015 -0700

    dpctl.at: Ignore string representation of error messages in output.
    
    Different C libraries represent the same error code &#40;particularly ENODEV&#41;
    differently.  This caused spurious test failures on BSD.  This commit
    avoids the problem by ignoring the error string representations entirely.
    
    Reported-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
</pre>
