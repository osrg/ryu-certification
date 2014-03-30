---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d25a34be-c4ff-4d9d-b62e-72a8c603ff70
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 111b536b-cb73-41eb-a921-a8cff3b50130
controller          : [82286791-b395-44bd-8b71-9604a3f1b920]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [75ba5485-9268-452d-abd3-abe05b90e0cb, 8be23206-4ee2-4e66-93b0-74a33cacfb5a, c5ebe9f2-72f5-4ba4-8fca-db2ebbf9ef44]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 82286791-b395-44bd-8b71-9604a3f1b920
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=306, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 75ba5485-9268-452d-abd3-abe05b90e0cb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3172b69c-fea6-4cd1-8633-a81c3d47775b]
name                : eth8

_uuid               : c5ebe9f2-72f5-4ba4-8fca-db2ebbf9ef44
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4b88f5f6-132a-48c6-a202-4f805581a0e6]
name                : eth7

_uuid               : 8be23206-4ee2-4e66-93b0-74a33cacfb5a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fd7bb7a9-7559-40e2-80e1-5843478fa9ea]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3172b69c-fea6-4cd1-8633-a81c3d47775b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6156667, tx_dropped=0, tx_errors=0, tx_packets=65629}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : fd7bb7a9-7559-40e2-80e1-5843478fa9ea
admin_state         : up
duplex              : full
ifindex             : 803
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

_uuid               : 4b88f5f6-132a-48c6-a202-4f805581a0e6
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
statistics          : {collisions=0, rx_bytes=3071550337, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72719335, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d81eef1b874c3c51669fa56f57e69ba5e77ad2c5
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Fri Mar 28 13:44:23 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Sat Mar 29 17:16:19 2014 -0700

    datapath: Minimize dp and vport critical sections.
    
    Move most memory allocations away from the ovs_mutex critical
    sections.  vport allocations still happen while the lock is taken, as
    changing that would require major refactoring. Also, vports are
    created very rarely so it should not matter.
    
    Change ovs_dp_cmd_get() now only takes the rcu_read_lock(), rather
    than ovs_lock(), as nothing need to be changed.  This was done by
    ovs_vport_cmd_get() already.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
