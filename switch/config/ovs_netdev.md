---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
74a529bd-6ab5-4d0c-a0c9-0ecd4328eb60
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 10799cfd-4ba7-4729-ac19-2725aa7b9fc1
controller          : [3d232d60-ef1d-4579-b326-9f064be59bf8]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [6c4c7382-c1e8-421b-a5d2-7faf6198bac2, 72e4243d-79f7-446b-8304-274ae72403c5, aa2a056d-b03c-4c05-b13d-96f3b1db8cb0, ffb9cbc0-2207-4f27-ba07-a9189ab29a2d]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3d232d60-ef1d-4579-b326-9f064be59bf8
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ffb9cbc0-2207-4f27-ba07-a9189ab29a2d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f89c9223-9ff6-43ba-aff7-0e642d705b25]
name                : "br0"

_uuid               : aa2a056d-b03c-4c05-b13d-96f3b1db8cb0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [200bbd96-28fa-4e9b-83d5-df5f8a6fa1df]
name                : "eth23"

_uuid               : 72e4243d-79f7-446b-8304-274ae72403c5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [65855481-78c9-4b92-aadd-31f165bd1bc2]
name                : "eth22"

_uuid               : 6c4c7382-c1e8-421b-a5d2-7faf6198bac2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8419b7dd-85ce-40ea-b58c-58ddcc31a09e]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8419b7dd-85ce-40ea-b58c-58ddcc31a09e
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=24024581534, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16026376, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 65855481-78c9-4b92-aadd-31f165bd1bc2
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18089315792, tx_dropped=0, tx_errors=0, tx_packets=12064077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 200bbd96-28fa-4e9b-83d5-df5f8a6fa1df
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1176922500, tx_dropped=0, tx_errors=0, tx_packets=784615}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f89c9223-9ff6-43ba-aff7-0e642d705b25
admin_state         : down
duplex              : full
ifindex             : 198
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit daab0ae6bb558411f24cee6a7bb32599a5f9e363
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Jun 23 11:38:56 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Jun 26 08:44:20 2015 -0700

    ofproto: Fix use-after-free in bridge destruction with groups.
    
    Groups were not destroyed until after lots of other important bridge
    data had been destroyed, including the connection manager.  There was an
    indirect dependency on the connection manager for bridge destruction
    because destroying a group also destroys all of the flows that reference
    the group, which in turn causes the ofmonitor to be invoked to report that
    the flows had been destroyed.  This commit fixes the problem by destroying
    groups earlier.
    
    The problem can be observed by reverting the code changes in this commit
    then running &quot;make check-valgrind&quot; with the test that this commit
    introduces.
    
    Reported-by: Simon Horman &lt;simon.horman@netronome.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Reviewed-by: Simon Horman &lt;simon.horman@netronome.com&gt;
</pre>
