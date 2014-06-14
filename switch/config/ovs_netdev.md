---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8bda0322-fa81-4f20-87f3-96ac35b2e2f5
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
_uuid               : 2872b402-4b68-4a98-abc0-a4e675426678
controller          : [ec13688e-3849-43d2-85f0-b9de46532d3e]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0ff58cea-f54d-41e1-8698-28ab51f8eeef, 279264a5-db03-401e-aea3-b328638d3860, 84cec106-a029-4dec-bd9f-99089435b325, c3ab04ef-d015-4d76-a48e-19d730df7663]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ec13688e-3849-43d2-85f0-b9de46532d3e
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=961, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 279264a5-db03-401e-aea3-b328638d3860
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0c76993a-0007-4fc0-b574-e97e04b776a3]
name                : eth23

_uuid               : 84cec106-a029-4dec-bd9f-99089435b325
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a23550b8-04d3-4342-a0c8-980e758b418e]
name                : eth21

_uuid               : 0ff58cea-f54d-41e1-8698-28ab51f8eeef
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [69d117e8-b4c3-4d26-b890-16e8dfcd7a39]
name                : br0

_uuid               : c3ab04ef-d015-4d76-a48e-19d730df7663
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [720699ad-a8ce-4fa4-b8b9-e9e730d06346]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a23550b8-04d3-4342-a0c8-980e758b418e
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
statistics          : {collisions=0, rx_bytes=3599854525, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28251568, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 69d117e8-b4c3-4d26-b890-16e8dfcd7a39
admin_state         : down
duplex              : full
ifindex             : 508
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

_uuid               : 720699ad-a8ce-4fa4-b8b9-e9e730d06346
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2628430946, tx_dropped=0, tx_errors=0, tx_packets=13236064}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0c76993a-0007-4fc0-b574-e97e04b776a3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3787250908, tx_dropped=0, tx_errors=0, tx_packets=8251457}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
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
