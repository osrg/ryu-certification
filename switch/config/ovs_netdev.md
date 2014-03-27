---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4b04777a-1527-48c0-8a6b-2e9acf153109
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
_uuid               : a1b27091-e1cd-4fff-9cdd-e1c7da0613b5
controller          : [a3d63c48-983c-4f5e-92d1-ddef10dd52fd]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [7484a12e-2779-42e4-b294-16e967d5923e, c1549bed-ac4b-41a0-9f64-0143d942fb21, de316b1d-d91e-4066-891a-cac1b3a8e33c]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a3d63c48-983c-4f5e-92d1-ddef10dd52fd
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=312, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : de316b1d-d91e-4066-891a-cac1b3a8e33c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9778734a-e90a-402d-b963-c069a2780889]
name                : br0

_uuid               : c1549bed-ac4b-41a0-9f64-0143d942fb21
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [16c1f2e9-0799-4587-b2b2-22c4aa54a36f]
name                : eth8

_uuid               : 7484a12e-2779-42e4-b294-16e967d5923e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c6e6fbe6-e862-48b6-a8b3-9fbbe1d91c47]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 16c1f2e9-0799-4587-b2b2-22c4aa54a36f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5744310, tx_dropped=0, tx_errors=0, tx_packets=61235}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : c6e6fbe6-e862-48b6-a8b3-9fbbe1d91c47
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
statistics          : {collisions=0, rx_bytes=3070132898, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72704926, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 9778734a-e90a-402d-b963-c069a2780889
admin_state         : up
duplex              : full
ifindex             : 755
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
commit b6c4da210dccd802d775a58af1b6eac2e866d011
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Mar 27 10:04:55 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Mar 27 10:05:36 2014 -0700

    stream-tcp: Fix error message for failed TCP_NODELAY setting on Windows.
    
    Reported-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Kyle Mestery &lt;mestery@noironetworks.com&gt;
    Acked-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
