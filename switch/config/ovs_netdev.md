---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
45213e87-fce5-4a5f-9a48-f3db36746279
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 650aae6a-1210-448f-8aa5-f481a42ca573
controller          : [a15ea7ea-10e0-49e5-9490-07220c448527]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [264155eb-59fc-4be2-9992-4db4ef64ad57, a882af16-2443-48f3-85d2-dfabad93a78c, b435728e-8534-4fc5-901a-ca8f2ce7496f, cb261ad6-74d5-432c-877c-a25b54ab59b7]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a15ea7ea-10e0-49e5-9490-07220c448527
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=567, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : cb261ad6-74d5-432c-877c-a25b54ab59b7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [62c1e52a-7ff3-459a-97d2-1a193c906202]
name                : br0

_uuid               : a882af16-2443-48f3-85d2-dfabad93a78c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [094a842d-395a-4f1c-bc10-abdf55a15147]
name                : eth21

_uuid               : b435728e-8534-4fc5-901a-ca8f2ce7496f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2971afc4-a2fd-4078-9ff5-91148f2685ec]
name                : eth22

_uuid               : 264155eb-59fc-4be2-9992-4db4ef64ad57
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0ea819ae-4cb1-4442-9b22-3d30de2048a5]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2971afc4-a2fd-4078-9ff5-91148f2685ec
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1376032646, tx_dropped=0, tx_errors=0, tx_packets=921109}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 094a842d-395a-4f1c-bc10-abdf55a15147
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
statistics          : {collisions=0, rx_bytes=3506086054, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2347355, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0ea819ae-4cb1-4442-9b22-3d30de2048a5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2480371500, tx_dropped=0, tx_errors=0, tx_packets=1653581}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 62c1e52a-7ff3-459a-97d2-1a193c906202
admin_state         : down
duplex              : full
ifindex             : 123
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
commit 9a7a91546f3eb7768662a54a930763935e3be3d6
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Tue May 20 11:07:02 2014 +0900
Commit:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
CommitDate: Wed May 21 15:21:34 2014 +0900

    FAQ: Add an entry about datapath-id
    
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
</pre>
