---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
de8288aa-9f77-45ca-be2a-15029db3242a
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 736bd674-af31-4920-ad8b-7e6907b6b4c6
controller          : [42b77104-18dc-4db3-b9ed-c8bbccbecde9]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1c7234a1-a7cc-4928-93bb-4220606d8d31, 86e81d7b-0300-451c-a798-93f71b5688ac, 8c2b818e-39ac-43c1-945d-c47958099c00, 914bbb9d-f8a0-4cb5-89fd-a1a357309de9]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 42b77104-18dc-4db3-b9ed-c8bbccbecde9
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=692, sec_since_disconnect=7, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 914bbb9d-f8a0-4cb5-89fd-a1a357309de9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [776ec66d-56de-40bd-9831-f161e2145972]
name                : br0

_uuid               : 1c7234a1-a7cc-4928-93bb-4220606d8d31
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dc48d487-98b9-410f-8c50-67830cfb5f7f]
name                : eth21

_uuid               : 8c2b818e-39ac-43c1-945d-c47958099c00
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2cc95513-ff2d-4e3c-981f-2a493b99f70f]
name                : eth23

_uuid               : 86e81d7b-0300-451c-a798-93f71b5688ac
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [04428f61-50f5-4659-84c3-cc57e43dd64c]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 776ec66d-56de-40bd-9831-f161e2145972
admin_state         : down
duplex              : full
ifindex             : 199
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

_uuid               : 04428f61-50f5-4659-84c3-cc57e43dd64c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3265681528, tx_dropped=0, tx_errors=0, tx_packets=48018197}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2cc95513-ff2d-4e3c-981f-2a493b99f70f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4055138204, tx_dropped=0, tx_errors=0, tx_packets=5566737}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : dc48d487-98b9-410f-8c50-67830cfb5f7f
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
statistics          : {collisions=0, rx_bytes=2349671067, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=76074408, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
