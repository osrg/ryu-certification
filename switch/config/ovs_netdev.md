---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d7b74b94-a86b-4bf9-b6c3-0c08709b68c6
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8702b35e-731e-468f-a38a-1aa475a5d5dc
controller          : [d82e8f31-5a86-4a84-9d15-8121ab122e2e]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [37383871-3593-45f9-a71c-a9a5ac19e2cf, 99f80c1c-64a7-4811-887d-7b6241e28c63, bebb2a33-d272-4c62-8ca5-fadbb4fd1c05, cf6ad8f8-d663-463e-8abd-f87bc53893df]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d82e8f31-5a86-4a84-9d15-8121ab122e2e
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=672, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : cf6ad8f8-d663-463e-8abd-f87bc53893df
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3da968e0-06ea-4926-9252-524b4b392836]
name                : eth21

_uuid               : 99f80c1c-64a7-4811-887d-7b6241e28c63
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [66e2166c-2e2c-4a82-9060-8236c39555de]
name                : eth23

_uuid               : 37383871-3593-45f9-a71c-a9a5ac19e2cf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8ce9001f-cb7c-4bf7-854c-c61f0d040360]
name                : eth22

_uuid               : bebb2a33-d272-4c62-8ca5-fadbb4fd1c05
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [89d156a9-15ef-466f-9499-db75b72e5ccb]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3da968e0-06ea-4926-9252-524b4b392836
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=2307708119, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=84604237, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 66e2166c-2e2c-4a82-9060-8236c39555de
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2895939000, tx_dropped=0, tx_errors=0, tx_packets=1930626}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 89d156a9-15ef-466f-9499-db75b72e5ccb
admin_state         : down
duplex              : full
ifindex             : 81
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 8ce9001f-cb7c-4bf7-854c-c61f0d040360
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1311359240, tx_dropped=0, tx_errors=0, tx_packets=49563541}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fb66fbd15b98e897841f326b6dd0842ba6bde1a9
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Tue Aug 5 13:49:57 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Wed Aug 6 22:12:25 2014 -0700

    datapath: Use tun_info only for egress tunnel path.
    
    Currently tun_info is used for passing tunnel information
    on ingress and egress path, this cause confusion.  Following
    patch removes its use on ingress path make it egress only parameter.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
