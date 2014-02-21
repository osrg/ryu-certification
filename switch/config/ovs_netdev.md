---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
564125d2-b88d-4dac-b356-9b62ef3a76e6
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
_uuid               : c203547e-1955-4086-b166-baff71ba49dc
controller          : [36695c94-efd7-4f68-90d0-3533bd5e10f5]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [14ce8d66-18a7-4b3d-a3d2-81484f4ff8d6, 4c9dc03a-65b1-4c19-bb63-85175fa572e0, 548771c1-d29b-4910-b49e-df3b027975e1]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 36695c94-efd7-4f68-90d0-3533bd5e10f5
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=372, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 548771c1-d29b-4910-b49e-df3b027975e1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ff9ebc9b-f3aa-4ce3-b22e-b3bc7a6a48e3]
name                : eth8

_uuid               : 4c9dc03a-65b1-4c19-bb63-85175fa572e0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8886b3b7-447d-4657-a5b0-590405ca31e8]
name                : eth7

_uuid               : 14ce8d66-18a7-4b3d-a3d2-81484f4ff8d6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d30675e2-b3f7-4910-8ddb-b7c3f8b5e384]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d30675e2-b3f7-4910-8ddb-b7c3f8b5e384
admin_state         : up
duplex              : full
ifindex             : 320
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

_uuid               : 8886b3b7-447d-4657-a5b0-590405ca31e8
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
statistics          : {collisions=0, rx_bytes=3059402803, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72596056, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : ff9ebc9b-f3aa-4ce3-b22e-b3bc7a6a48e3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2581888, tx_dropped=0, tx_errors=0, tx_packets=27563}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 66679738c19b7597f4db93266181463709cade57
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Feb 21 08:45:03 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Feb 21 08:45:44 2014 -0800

    FAQ: Describe how to add new OpenFlow messages.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
