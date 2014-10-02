---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e4cb22d3-d5e3-4feb-8b56-d28a20cf149c
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8ea5acb0-2fab-42cf-a6a1-c3409f0aa1c9
controller          : [96bb85a4-504b-4e52-a29d-596f68484253]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [35ce0994-64c5-4b32-b26a-122936fc98f4, 5d842574-cfb4-404f-9d2b-27f89c63c6d8, a7158829-4efa-4ba0-9b1d-ecd0b1f87e48, b57c2666-d999-4fae-a32b-522d300095dd]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 96bb85a4-504b-4e52-a29d-596f68484253
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=677, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 35ce0994-64c5-4b32-b26a-122936fc98f4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c894a543-4d8e-41b1-8054-0d3cc7bd31b2]
name                : eth23

_uuid               : 5d842574-cfb4-404f-9d2b-27f89c63c6d8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [62b3d79b-c523-4cc9-93d0-d5854b5a080c]
name                : eth21

_uuid               : a7158829-4efa-4ba0-9b1d-ecd0b1f87e48
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [91e9b0a9-2c5b-49d8-91fc-3e4eb33d5b9f]
name                : br0

_uuid               : b57c2666-d999-4fae-a32b-522d300095dd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a54fa332-90ac-45c0-82b5-a676a4473335]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 91e9b0a9-2c5b-49d8-91fc-3e4eb33d5b9f
admin_state         : down
duplex              : full
ifindex             : 197
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

_uuid               : a54fa332-90ac-45c0-82b5-a676a4473335
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3213358368, tx_dropped=0, tx_errors=0, tx_packets=47983022}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c894a543-4d8e-41b1-8054-0d3cc7bd31b2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3967197704, tx_dropped=0, tx_errors=0, tx_packets=5508110}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 62b3d79b-c523-4cc9-93d0-d5854b5a080c
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
statistics          : {collisions=0, rx_bytes=2232764359, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=75995839, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 01420a2cddd7b5cf0a8ac59a4d60ce9d3b328d97
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Wed Oct 1 10:38:23 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Thu Oct 2 09:18:30 2014 -0700

    stream-tcp: Change the connection name for pwindows.
    
    As of now, when someone passes a punix:foo/bar as a connection type
    in Windows, we create a TCP server using 127.0.0.1 and save the kernel
    assigned port number in the file foo/bar. The connection name
    as obtained through pstream_get_name&#40;&#41; would be ptcp:127.0.0.1:.
    This was okay if pstream_get_name&#40;&#41; was only used for logging
    purposes. But netdev-dummy uses it to close active connections when the
    passed name and created name are different. This causes transient
    connection teardowns while using patch ports in Windows unit tests
    causing occasional packet loss.
    
    This commit sets the connection name to be punix:foo/bar instead
    of ptcp:127.0.0.1: for pwindows.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
