---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f9376f16-8c94-4afd-b3a8-ab2c46fb49fc
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8f755b9a-3b54-4509-b927-6a7fdb4c7deb
controller          : [2fec08fe-1746-407e-9e51-59070472e899]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2c277bd4-5ceb-4edd-9c28-730a42212beb, 6e588a2e-3c26-4453-8443-1e008d28f76c, a49852c9-1273-430e-90a5-40d699f2d2ad, cc27ef23-dbfe-4bcb-ae2d-c49dcaf2cfe4]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2fec08fe-1746-407e-9e51-59070472e899
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=557, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2c277bd4-5ceb-4edd-9c28-730a42212beb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [243f4404-a973-4bd5-a91c-d0c8df238feb]
name                : eth21

_uuid               : a49852c9-1273-430e-90a5-40d699f2d2ad
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aa335ec3-849b-4e2d-8cdc-6ff73a2b6133]
name                : eth22

_uuid               : 6e588a2e-3c26-4453-8443-1e008d28f76c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f9df5290-ae82-418b-9d73-72dd6fd0f9dd]
name                : br0

_uuid               : cc27ef23-dbfe-4bcb-ae2d-c49dcaf2cfe4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1030af91-98b3-4304-aba5-017dc0ab0b2b]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 243f4404-a973-4bd5-a91c-d0c8df238feb
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
statistics          : {collisions=0, rx_bytes=2159444932, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1451938, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f9df5290-ae82-418b-9d73-72dd6fd0f9dd
admin_state         : down
duplex              : full
ifindex             : 152
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

_uuid               : 1030af91-98b3-4304-aba5-017dc0ab0b2b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1379785500, tx_dropped=0, tx_errors=0, tx_packets=919857}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : aa335ec3-849b-4e2d-8cdc-6ff73a2b6133
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=958445624, tx_dropped=0, tx_errors=0, tx_packets=643474}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 97a360ced33fe81e29a585aa29b3c7c90c916835
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Tue May 13 14:46:18 2014 +0900
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Tue May 13 13:39:53 2014 -0700

    datapath: Free skb&#40;s&#41; on recirculation error
    
    This patch attempts to ensure that skb&#40;s&#41; are always freed &#40;once&#41;
    if if an error occurs in execute_recirc&#40;&#41;. It does so in two ways:
    
    1. Ensure that execute_recirc&#40;&#41; always consimes skb passed to it.
       Specifically, free the skb if the call to ovs_flow_extract&#40;&#41; fails.
    
    2. Return from the recirc case in execute_recirc&#40;&#41; whenever
       the skb has not been cloned immediately above.
    
       This is only the case if the action is both the last action and the
       keep_skb parameter of execute_recirc is not true.  As it is the last
       action and the skb is consumed one way or another by execute_recirc&#40;&#41; it
       is correct to return here.  In particular this avoids the possibility of
       the skb, which has been consumed by execute_recirc&#40;&#41; from being freed.
    
       Conversely if this is not the case then the skb has been cloned
       and the clone has been consumed by execute_recirc&#40;&#41;.
       This leads to three sub-cases:
       * If execute_recirc&#40;&#41; returned an error code then the original skb
         will be freed by the error handling code below the case statement in
         do_execute_actions&#40;&#41;.
       * If this is not the last action then action processing will continue,
         using the original skb.
       * If this is the last action then it must also be the case that keep_skb
         is true &#40;otherwise the skb would not have been cloned&#41;. Thus
         do_execute_actions&#40;&#41; will return without freeing the original skb.
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    [jesse: use kfree_skb instead of consume_skb on error path]
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
