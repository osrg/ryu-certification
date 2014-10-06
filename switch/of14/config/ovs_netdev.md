---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c44f1c24-220a-445f-acff-aa382eacd9b3
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 81066356-9f83-4010-8d82-1a8973045245
controller          : [039bbf24-7188-413d-b0f9-6fa51e9a9f1a]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [853d0403-df04-4eb1-bde6-1a2cb9a6b8e8, b647330f-31a8-4d17-aab8-657ea2ae1e00, bf633e7c-df5c-4ea7-9524-f0db71b503d2, c1babd4e-d7a9-4cfc-bf43-4f7f64394ef6]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 039bbf24-7188-413d-b0f9-6fa51e9a9f1a
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=672, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : bf633e7c-df5c-4ea7-9524-f0db71b503d2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d03b17eb-52e5-4e2c-9291-3e1a21279919]
name                : br0

_uuid               : c1babd4e-d7a9-4cfc-bf43-4f7f64394ef6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3447f596-530a-4713-890d-ddcff77c607d]
name                : eth23

_uuid               : 853d0403-df04-4eb1-bde6-1a2cb9a6b8e8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6b947257-73e1-4a97-bf81-25b8ae360274]
name                : eth22

_uuid               : b647330f-31a8-4d17-aab8-657ea2ae1e00
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ce5f4f7d-c92c-4f9e-99cc-1360c3ebdfd4]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ce5f4f7d-c92c-4f9e-99cc-1360c3ebdfd4
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
statistics          : {collisions=0, rx_bytes=3156177287, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=108116169, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3447f596-530a-4713-890d-ddcff77c607d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=447485908, tx_dropped=0, tx_errors=0, tx_packets=6024947}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d03b17eb-52e5-4e2c-9291-3e1a21279919
admin_state         : down
duplex              : full
ifindex             : 211
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

_uuid               : 6b947257-73e1-4a97-bf81-25b8ae360274
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3138357324, tx_dropped=0, tx_errors=0, tx_packets=62253024}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit b3fca241bc3ecde81da6f6136f3dd0f1604a7412
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Mon Oct 6 10:16:34 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Mon Oct 6 13:47:33 2014 -0700

    ovs-vswitchd: Add a missing headline in documentation.
    
    The logging options were shown as part of the &quot;Public Key Infrastructure
    Options&quot;. Correct it.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
