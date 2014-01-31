---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f183ae5b-2d00-4d70-95fa-fd583496b6c6
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 78467229-12a6-4221-a0f9-dbf4ff39fa14
controller          : [e148e88f-fa31-4b89-95b9-62a6fcab9978]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0bd3ba20-eef2-4ee8-a355-a37248d79082, 1c715b3e-9f1c-4a63-933e-8f25f9f89fd6, 546f61c9-ad0f-4acc-934b-bf32029960e6]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e148e88f-fa31-4b89-95b9-62a6fcab9978
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=301, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0bd3ba20-eef2-4ee8-a355-a37248d79082
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0f5bb79c-ed7b-4c87-b08a-6a6bf430449c]
name                : br0

_uuid               : 546f61c9-ad0f-4acc-934b-bf32029960e6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [caa2b6f9-3c4a-4d17-b139-cf0144eb0913]
name                : eth8

_uuid               : 1c715b3e-9f1c-4a63-933e-8f25f9f89fd6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3e72dc42-3220-42ca-a912-6c9cc8ac19f9]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0f5bb79c-ed7b-4c87-b08a-6a6bf430449c
admin_state         : up
duplex              : full
ifindex             : 96
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

_uuid               : caa2b6f9-3c4a-4d17-b139-cf0144eb0913
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=540778, tx_dropped=0, tx_errors=0, tx_packets=5778}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 3e72dc42-3220-42ca-a912-6c9cc8ac19f9
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
statistics          : {collisions=0, rx_bytes=3053125144, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72532676, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 59804c80a9821e3aca208012c1a496f3c26bfe9a
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Jan 30 16:57:16 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jan 30 16:57:16 2014 -0800

    bridge: Set ofport column in every database transaction.
    
    Database transactions can occasionally fail due to concurrent changes in
    the database.  When that happens, the next transaction should repeat the
    changes that ovs-vswitchd tried to make the first time (adjusted for the
    changes to the database).
    
    The code to report the OpenFlow port number in use didn't do that.  It set
    the ofport field once when it created the port and never set it again, even
    if the transaction to set it failed.  This commit fixes the problem.
    
    Bug #23047.
    Reported-by: Suganya Ramachandran &lt;suganyar@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
