---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
21c74e85-8a1e-4229-9503-18220412e786
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7db14bc6-bbc1-43a9-9282-28ae32bce639
controller          : [f36759ac-0afe-44b1-b91a-b3b2ec464c88]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [22cc81f7-3cae-49a2-a3df-08c71f3b200a, 750094c6-f633-47bd-bc48-bc7efebe119d, a2f31af1-66ca-4192-9157-cf17d1982b4d, fa2a95f8-97d1-4b24-a089-f5f088c55de3]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f36759ac-0afe-44b1-b91a-b3b2ec464c88
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=982, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : fa2a95f8-97d1-4b24-a089-f5f088c55de3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0ad6d4b5-30cb-4c30-bc6c-22ff3b419d0a]
name                : eth21

_uuid               : a2f31af1-66ca-4192-9157-cf17d1982b4d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aae2ff72-8f14-42f4-93f5-c9827d04a993]
name                : br0

_uuid               : 750094c6-f633-47bd-bc48-bc7efebe119d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [76197b69-2bae-4a75-8269-57deaa331704]
name                : eth22

_uuid               : 22cc81f7-3cae-49a2-a3df-08c71f3b200a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b34d3087-21e3-4836-ba2a-ccc789b08d98]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 76197b69-2bae-4a75-8269-57deaa331704
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2342801378, tx_dropped=0, tx_errors=0, tx_packets=35973613}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0ad6d4b5-30cb-4c30-bc6c-22ff3b419d0a
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
statistics          : {collisions=0, rx_bytes=3805446048, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=91435015, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : aae2ff72-8f14-42f4-93f5-c9827d04a993
admin_state         : down
ifindex             : 698
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : b34d3087-21e3-4836-ba2a-ccc789b08d98
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=1815805284, tx_dropped=0, tx_errors=0, tx_packets=12664467}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 72d96679c14988f3267135459aba7333d0ec32a0
Author:     Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
AuthorDate: Tue Jun 24 16:08:34 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Wed Jun 25 10:54:06 2014 -0700

    dpif-netdev: Delete packet if not able to do upcall
    
    In dp_netdev_input&#40;&#41; we nevered fully covered the case where handler queues are
    not there.
    With this change we increment the stat counter and free the packet.
    
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
