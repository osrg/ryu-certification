---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
285d0bd9-2685-4f7e-bd96-24fb869f0bbe
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 2ee24ce8-3541-40af-819b-42042a6194ea
controller          : [ae1a2b40-ae2f-4d4d-a12a-020734d0571f]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [40ed6283-8479-469a-bcfc-7d2c5781218c, 7315139a-c094-497d-9cc2-ee56e0b36cea, 7ac2263a-4257-48da-b41c-7a74ad3f2637, b4b9a254-ab7a-4a9d-914c-6c1dafcbbccd]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ae1a2b40-ae2f-4d4d-a12a-020734d0571f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=727, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b4b9a254-ab7a-4a9d-914c-6c1dafcbbccd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [764a83e3-ee9c-4459-ad54-e1fde6b9394f]
name                : eth22

_uuid               : 7315139a-c094-497d-9cc2-ee56e0b36cea
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7ffa9582-5d35-4f67-8922-3b450434bcc5]
name                : eth23

_uuid               : 7ac2263a-4257-48da-b41c-7a74ad3f2637
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e6ea0509-5d74-4c3e-8bd3-c224a7a32655]
name                : eth21

_uuid               : 40ed6283-8479-469a-bcfc-7d2c5781218c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9fde34d6-5a4e-4c44-be51-e4cb1f7f5dd6]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e6ea0509-5d74-4c3e-8bd3-c224a7a32655
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
statistics          : {collisions=0, rx_bytes=3186166533, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=171158559, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9fde34d6-5a4e-4c44-be51-e4cb1f7f5dd6
admin_state         : down
duplex              : full
ifindex             : 291
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

_uuid               : 7ffa9582-5d35-4f67-8922-3b450434bcc5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4265201908, tx_dropped=0, tx_errors=0, tx_packets=8570091}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 764a83e3-ee9c-4459-ad54-e1fde6b9394f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2886626152, tx_dropped=0, tx_errors=0, tx_packets=105048330}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit b1b72f2de4141017ee230d889c23d0e3ffc297a2
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Mon Oct 27 10:57:28 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Mon Oct 27 13:15:35 2014 -0700

    lib/ovs-rcu: Support static initialization.
    
    Currently, OVSRCU_TYPE_INITIALIZER always initializes the RCU pointer
    as NULL.  There is no reason why the RCU pointer could not be
    initialized with a non-NULL value, however, as statically allocated
    memory is even more stable than required for RCU.
    
    This patch changes the initializer to OVSRCU_INITIALIZER&#40;VALUE&#41;, which
    can take any pointer value as a parameter.
    
    This allows rculist, which is introduced in a following patch, to
    provide an initializer similar to the one in the normal list.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
