---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
74a317d8-232b-4140-85be-a41423639d46
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f9a970e9-fdbc-4b7f-a99d-e50ee619a658
controller          : [63b13ead-77fb-481b-9c1a-c10d4074a8be]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [25352f5a-57f1-4e30-9547-95cd95a93aac, 4956bd9c-1b76-4b5c-8747-22831d425d28, 6f340d01-b184-43a4-843c-e848020e200f]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 63b13ead-77fb-481b-9c1a-c10d4074a8be
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=376, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4956bd9c-1b76-4b5c-8747-22831d425d28
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ca01d4ac-7e25-481d-8284-120ae0937031]
name                : br0

_uuid               : 6f340d01-b184-43a4-843c-e848020e200f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d0746d1d-3c22-47f2-bb60-09a746956351]
name                : eth8

_uuid               : 25352f5a-57f1-4e30-9547-95cd95a93aac
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [75eeb7c9-a1bc-4914-8604-6de8d5bda3c0]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ca01d4ac-7e25-481d-8284-120ae0937031
admin_state         : up
duplex              : full
ifindex             : 405
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

_uuid               : 75eeb7c9-a1bc-4914-8604-6de8d5bda3c0
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
statistics          : {collisions=0, rx_bytes=3060895461, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72611223, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : d0746d1d-3c22-47f2-bb60-09a746956351
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3014692, tx_dropped=0, tx_errors=0, tx_packets=32174}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
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
