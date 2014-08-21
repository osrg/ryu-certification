---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
cfa1281e-8342-41f0-ba14-7b65e0c8f4ed
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 12527501-01d7-482c-899d-7c7a9a383bd9
controller          : [4e8907bd-f0ae-41b6-99f7-c607b0f6eb65]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [35c9f681-c6ed-4783-9cb9-9ce671b1c39f, 768cbdfb-8e96-4d8a-8d96-a8910d23eae3, 7bb7c3b4-e76f-4939-a97a-494ee398069b, 8956397d-0d12-4d5b-bab4-88045a4b98af]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4e8907bd-f0ae-41b6-99f7-c607b0f6eb65
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=661, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7bb7c3b4-e76f-4939-a97a-494ee398069b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [49581729-606d-4ad3-999b-010aae8530e2]
name                : eth23

_uuid               : 8956397d-0d12-4d5b-bab4-88045a4b98af
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [49924cb6-2669-4a44-bb48-8a32c886132d]
name                : br0

_uuid               : 35c9f681-c6ed-4783-9cb9-9ce671b1c39f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a03ef5da-f493-4ecf-b322-1c154cfeec4e]
name                : eth22

_uuid               : 768cbdfb-8e96-4d8a-8d96-a8910d23eae3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f96b4520-18ae-4042-a538-580e8f0517de]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f96b4520-18ae-4042-a538-580e8f0517de
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
statistics          : {collisions=0, rx_bytes=2482570235, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1662224, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 49581729-606d-4ad3-999b-010aae8530e2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1044349500, tx_dropped=0, tx_errors=0, tx_packets=696233}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a03ef5da-f493-4ecf-b322-1c154cfeec4e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1163750440, tx_dropped=0, tx_errors=0, tx_packets=779084}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 49924cb6-2669-4a44-bb48-8a32c886132d
admin_state         : down
duplex              : full
ifindex             : 47
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1a12c419bdbc4a2d458eb8fa07118b4bfc9e0a4f
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed Aug 20 22:22:58 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Aug 21 09:08:03 2014 -0700

    ovs-ofctl: Document that &quot;move&quot; uses a standard action in OF1.5+.
    
    Reported-by: Jean Tourrilhes &lt;jt@hpl.hp.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Jean Tourrilhes &lt;jt@hpl.hp.com&gt;
</pre>
