---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e84af8b8-d43a-4dcb-94fe-ed3aea04fc0d
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
_uuid               : 209dc832-6fdc-49ac-9178-a93102a0f685
controller          : [3159f332-7e15-4335-9c8d-a3b1ae84d406]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [28f44692-0d17-40ff-bf4f-0cecd1ed4432, 34443112-dc9e-43ab-aea9-065c279ecc1c, 7196e569-567b-468f-8234-e30a419ee4e5]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3159f332-7e15-4335-9c8d-a3b1ae84d406
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=302, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7196e569-567b-468f-8234-e30a419ee4e5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [63c08038-fb89-40e4-9d01-bdef2bc2b93d]
name                : eth8

_uuid               : 28f44692-0d17-40ff-bf4f-0cecd1ed4432
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [96637526-ee62-4cde-bd35-089a32e3be6e]
name                : eth7

_uuid               : 34443112-dc9e-43ab-aea9-065c279ecc1c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e31c80ee-0010-4841-8e46-29a0f6464533]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 63c08038-fb89-40e4-9d01-bdef2bc2b93d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=592124, tx_dropped=0, tx_errors=0, tx_packets=6380}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 96637526-ee62-4cde-bd35-089a32e3be6e
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
statistics          : {collisions=0, rx_bytes=1892685, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=19140, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : e31c80ee-0010-4841-8e46-29a0f6464533
admin_state         : up
duplex              : full
ifindex             : 85
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
commit 69555fc1014349e6044ecd67846a18140bd5b954
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed Jan 15 12:37:04 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jan 16 12:48:42 2014 -0800

    ofproto-dpif-monitor: Change global rwlock into mutex.
    
    Nothing ever took monitor_rwlock's read lock, so it might as well be a
    mutex.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
