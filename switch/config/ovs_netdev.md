---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
89c04c6a-81e1-4484-8fae-7a2ba66918a6
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e42e33dd-c6ce-4a5c-91cc-9a26910d8166
controller          : [da1a9bc2-3785-41b5-8ea5-3def5f6e1058]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0469df0f-1f3e-4f7d-99d0-7106a3037e04, 1d69e8d5-712c-4a28-9963-488575ad5188, 560ea670-1ad5-4dc6-99f6-fbacd7646969, f1ef313f-17b0-4e62-af82-70ed72aa7f8e]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : da1a9bc2-3785-41b5-8ea5-3def5f6e1058
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=657, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 560ea670-1ad5-4dc6-99f6-fbacd7646969
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [74e70017-622a-4783-b295-86e852df6886]
name                : eth21

_uuid               : 1d69e8d5-712c-4a28-9963-488575ad5188
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [615878de-47b0-4312-83c1-0394bbdcaeae]
name                : br0

_uuid               : f1ef313f-17b0-4e62-af82-70ed72aa7f8e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b60fdfd8-0fac-4a3e-99ea-ff6989785fe7]
name                : eth22

_uuid               : 0469df0f-1f3e-4f7d-99d0-7106a3037e04
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1f83aef0-57eb-4c05-bdcf-72665fcd7043]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1f83aef0-57eb-4c05-bdcf-72665fcd7043
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=3255526284, tx_dropped=0, tx_errors=0, tx_packets=13624281}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b60fdfd8-0fac-4a3e-99ea-ff6989785fe7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2971819272, tx_dropped=0, tx_errors=0, tx_packets=36396763}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 615878de-47b0-4312-83c1-0394bbdcaeae
admin_state         : down
duplex              : full
ifindex             : 727
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

_uuid               : 74e70017-622a-4783-b295-86e852df6886
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
statistics          : {collisions=0, rx_bytes=1252191582, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=92605386, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f8003b53247ba837ee21ecef85c923124318fef8
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Wed Jun 25 11:06:18 2014 +0900
Commit:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
CommitDate: Thu Jun 26 12:52:41 2014 +0900

    FAQ: add an entry for MAC learning + VLAN
    
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Flavio Leitner &lt;fbl@redhat.com&gt;
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
</pre>
