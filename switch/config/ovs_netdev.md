---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
445d9622-d8b7-4d29-977c-bed88cb35f68
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 6ffaea40-7de1-466c-b995-e496dce4151e
controller          : [b58dfa9a-a4b9-475a-a80b-39478c428640]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [05961af5-0be0-45db-97ec-3ec7052f91e9, 739ca3a2-6693-4bf7-abbf-a04cc9d0981b, b136f80b-ad70-4885-bb64-cc7eaf187be7, fde41772-5296-4502-af13-4083d0140222]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b58dfa9a-a4b9-475a-a80b-39478c428640
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=967, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 05961af5-0be0-45db-97ec-3ec7052f91e9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [88aa23a7-fffa-4d31-bd5f-bd5b62a12673]
name                : eth22

_uuid               : fde41772-5296-4502-af13-4083d0140222
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [de458de4-42e2-441c-9c59-46c59fe7fc26]
name                : br0

_uuid               : 739ca3a2-6693-4bf7-abbf-a04cc9d0981b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0854a8e3-a310-457e-9366-cc2e796caa18]
name                : eth23

_uuid               : b136f80b-ad70-4885-bb64-cc7eaf187be7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [21defa12-c9f2-4bfc-a8af-bd6c7bbf8411]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : de458de4-42e2-441c-9c59-46c59fe7fc26
admin_state         : down
duplex              : full
ifindex             : 340
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

_uuid               : 21defa12-c9f2-4bfc-a8af-bd6c7bbf8411
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
statistics          : {collisions=0, rx_bytes=3048429954, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=10668399, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0854a8e3-a310-457e-9366-cc2e796caa18
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3499587704, tx_dropped=0, tx_errors=0, tx_packets=5196370}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 88aa23a7-fffa-4d31-bd5f-bd5b62a12673
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2598356644, tx_dropped=0, tx_errors=0, tx_packets=4611972}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7e5f06c31f34c7472e5c6a304a4ea56caf6cea82
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Tue Jun 3 08:35:16 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Tue Jun 3 08:37:45 2014 -0700

    lib/ovs-rcu: Rename ovsrcu_init&#40;&#41; as ovsrcu_set_hidden&#40;&#41;.
    
    ovsrcu_init&#40;&#41; was named after the atomic_init&#40;&#41;, but the semantics are
    different enough to warrant a different name.  Basically C11
    atomic_init is defined in a way that allows the implementation to
    assign the value without any syncronization, so in theory stores via
    atomic_init could be seen by others after stores via atomic_set, even
    if the atomic_init appeared earlier in the code.
    
    ovsrcu_set_hidden&#40;&#41; can be used to set an RCU protected variable when
    it is not yet accessible by any active reader, but will be made
    visible later via an ovsrcu_set call on some other pointer.
    
    This patch also adds a new ovsrcu_init&#40;&#41; that can be used to initilize
    RCU protected variables when the readers are not yet executing.  The
    new ovsrcu_init&#40;&#41; is implemented with atomic_init&#40;&#41;, so it does not
    provide any kind of syncronization.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
</pre>
