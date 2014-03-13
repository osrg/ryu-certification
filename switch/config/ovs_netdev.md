---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
03d5af24-4af2-4da6-b61a-d3fac34b30c5
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : acfb3033-ebf7-4191-a2a4-8ce3d4cfc21d
controller          : [801d192a-67c8-40f4-bf5d-a4c45a516363]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [26fb4be0-47a5-4aa7-b43d-451fc98612b6, 6fa4c631-6ade-4a68-97e3-e07459b0090f, 8c0e7114-4c28-4bf5-9863-6a1113114ba5]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 801d192a-67c8-40f4-bf5d-a4c45a516363
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=372, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 26fb4be0-47a5-4aa7-b43d-451fc98612b6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [40993401-89b4-403d-a21a-ea73ecbced7d]
name                : eth7

_uuid               : 8c0e7114-4c28-4bf5-9863-6a1113114ba5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7b85c568-d6ac-437f-8341-fa2c31e3e01b]
name                : eth8

_uuid               : 6fa4c631-6ade-4a68-97e3-e07459b0090f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3148891a-ec9b-4c1e-a392-73871f5b642f]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7b85c568-d6ac-437f-8341-fa2c31e3e01b
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3668560, tx_dropped=0, tx_errors=0, tx_packets=39139}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 40993401-89b4-403d-a21a-ea73ecbced7d
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=3063128882, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72633900, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 3148891a-ec9b-4c1e-a392-73871f5b642f
admin_state         : up
duplex              : full
ifindex             : 504
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1d7c9c6573827505da9b574507e69e7a69069cab
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Wed Mar 12 09:47:57 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Thu Mar 13 14:26:19 2014 -0700

    windows/sys: Define sa_family_t for easy compilation.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
