---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6260d5a6-b39a-4112-a39a-576931b9d7e3
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : cd6ab632-662f-4e39-8806-9be6991df36e
controller          : [78ba4873-d530-4902-a758-1f651656e895]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [777efe68-8725-4ff8-86cd-575f6df0db90, 8c703019-b487-4a8e-9372-7d0b35a087f1, be0fdaf7-84f7-4b47-8657-1c4379285ce0, d6dd871f-8007-4e8f-b21c-95e7abc88a02]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 78ba4873-d530-4902-a758-1f651656e895
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=677, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 777efe68-8725-4ff8-86cd-575f6df0db90
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [422b3916-fb3e-40a7-9386-1cac0c599b05]
name                : br0

_uuid               : 8c703019-b487-4a8e-9372-7d0b35a087f1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ba80de6a-0317-4057-8684-7764f5d75f80]
name                : eth22

_uuid               : d6dd871f-8007-4e8f-b21c-95e7abc88a02
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [da7c15d4-5899-4f8f-a55a-fec7f1cca8f6]
name                : eth23

_uuid               : be0fdaf7-84f7-4b47-8657-1c4379285ce0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [91876ebd-75a1-4280-b7f4-a5f9c00a6376]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : da7c15d4-5899-4f8f-a55a-fec7f1cca8f6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1365428204, tx_dropped=0, tx_errors=0, tx_packets=3773597}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 91876ebd-75a1-4280-b7f4-a5f9c00a6376
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
statistics          : {collisions=0, rx_bytes=3482514078, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=65356105, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ba80de6a-0317-4057-8684-7764f5d75f80
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3750397304, tx_dropped=0, tx_errors=0, tx_packets=45468791}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 422b3916-fb3e-40a7-9386-1cac0c599b05
admin_state         : down
duplex              : full
ifindex             : 140
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
commit 5e2a670201c936e0a1f8257f4540654f8b8bfed2
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Tue Sep 16 12:45:42 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Sep 16 08:11:31 2014 -0700

    ofproto-dpif-xlate: Suppress some warnings on non-Linux OSes
    
    These warnings were introduced by
    commit 7d031d7e511aeea8dd45348922fe8e3bbdd2956e
    &#40;&quot;ofproto-dpif-xlate: Work around Linux netdev_max_backlog limit.&quot;&#41;
    and found by --enable-Werror build on NetBSD.
    
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
