---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
eb37675f-e17a-4ab4-afeb-80c5a6ef00f0
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 6e66cb66-9e8f-4565-b3c3-53739f7552aa
controller          : [ad63ef55-f40e-492d-9451-c8c3e50c1a1c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [e693d226-0ea0-4ac2-844f-23f28be62029, e8ff91ef-e1dc-4178-a743-2b3e3189d5dd, fbf4add6-30dd-47f7-b824-12faae817716]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ad63ef55-f40e-492d-9451-c8c3e50c1a1c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=377, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : fbf4add6-30dd-47f7-b824-12faae817716
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [60c004c3-d53b-4ec0-b846-eb64bb9c85fd]
name                : br0

_uuid               : e693d226-0ea0-4ac2-844f-23f28be62029
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ddabcaa6-270f-4c5d-90f2-7649dbbf3436]
name                : eth7

_uuid               : e8ff91ef-e1dc-4178-a743-2b3e3189d5dd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [54320dc5-bf2f-4ee0-aa48-10305b95b8d3]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 54320dc5-bf2f-4ee0-aa48-10305b95b8d3
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3039038, tx_dropped=0, tx_errors=0, tx_packets=32434}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : ddabcaa6-270f-4c5d-90f2-7649dbbf3436
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=3060978300, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72612067, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 60c004c3-d53b-4ec0-b846-eb64bb9c85fd
admin_state         : up
duplex              : full
ifindex             : 413
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
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
commit 77587e0fef5818b5a873932c573781a14eb9edfb
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Feb 28 16:20:17 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Feb 28 18:15:02 2014 -0800

    vconn: Fix vconn_get_status() return value when connection in progress.
    
    When a connection takes a few rounds of the state machine to complete,
    'error' gets filled with EAGAIN until that completes.  This didn't match
    the vconn_get_status() documentation, which says that it only returns a
    positive errno value if there was an error.  One could fix the problem
    by updating the documentation (and the callers) or by updating the
    implementation.  I decided that the latter was the way to go because
    the distinction between the TCP connection being in progress or complete
    isn't visible to the client; what is visible to the client is the OpenFlow
    negotiation being complete.
    
    This problem is difficult to find in the unit tests because TCP connections
    to localhost complete immediately.
    
    Bug introduced by commit accaecc419cc57d (rconn: Discover errors in
    rconn_run() even if rconn_recv() is never called.)
    
    Reported-by: Anuprem Chalvadi &lt;achalvadi@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
