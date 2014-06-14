---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f9c0c3f0-e466-4711-95d5-e8f5fe3934d2
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
_uuid               : 677acb91-a04a-46e1-9f48-1b810e201fa1
controller          : [b2b3cba7-3b56-4ecc-8a2e-5731cb703291]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0f22ee54-8c72-491c-a4c7-a2b16d805d66, 1dd6a7f3-27b6-412a-8f61-2f10c55048b8, 6a83283d-caa4-4a7b-aa0b-8f31f1fc767e, 6b62d693-5b88-4a75-ba42-2f33994fac62]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b2b3cba7-3b56-4ecc-8a2e-5731cb703291
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=967, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0f22ee54-8c72-491c-a4c7-a2b16d805d66
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6bae322e-f2b9-473a-a2c4-cd62c8a5fe56]
name                : eth21

_uuid               : 6a83283d-caa4-4a7b-aa0b-8f31f1fc767e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [399eb99d-3afb-4036-bd9f-892e443556f8]
name                : eth22

_uuid               : 6b62d693-5b88-4a75-ba42-2f33994fac62
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ab47b92d-9dfa-4f70-ba04-249c798bdee7]
name                : eth23

_uuid               : 1dd6a7f3-27b6-412a-8f61-2f10c55048b8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ff5e7363-2fd7-462b-b40c-b1dc14faeb6e]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 399eb99d-3afb-4036-bd9f-892e443556f8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2669118816, tx_dropped=0, tx_errors=0, tx_packets=13263422}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ab47b92d-9dfa-4f70-ba04-249c798bdee7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3886766908, tx_dropped=0, tx_errors=0, tx_packets=8317801}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6bae322e-f2b9-473a-a2c4-cd62c8a5fe56
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
statistics          : {collisions=0, rx_bytes=3716707367, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28330096, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ff5e7363-2fd7-462b-b40c-b1dc14faeb6e
admin_state         : down
duplex              : full
ifindex             : 512
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
commit 15c9fbd8f28f907776db0f594a25ea94bf890978
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Fri May 30 10:19:26 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Fri Jun 13 17:47:32 2014 -0700

    bridge: Make ovs-vswitchd run again if status_txn commit fails.
    
    This commit adds logic that checks the return value of status_txn
    transaction and runs the update again if the transaction fails
    &#40;transaction status is not 'TXN_SUCCESS', 'TXN_UNCHANGED', or
    'TXN_INCOMPLETE'&#41;.
    
    To keep the code simple, the re-run of update on transaction failure
    will extracts the status from all interfaces, rather than just those
    that have status change.  Since the transaction failure is considered
    to be very rare, such overhead is deemed to be affordable.
    
    VMware-BZ: 1256577
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
