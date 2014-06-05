---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f5dc7cbc-3243-4ec8-bcb0-d2088f64bdb4
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ca54221c-ab76-4925-a911-bc9010801d30
controller          : [5096676e-cfab-449d-b912-3f2722e7b3e3]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [21b40cf8-6e19-4374-be4a-13d768e04daa, 86213118-4a39-43c2-9776-784f9352aa2d, 9e21e1f7-f9d8-40f3-b899-093945f2b8e2, fcd4ddc2-2c2b-4052-96b9-27b546e25654]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5096676e-cfab-449d-b912-3f2722e7b3e3
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=966, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 86213118-4a39-43c2-9776-784f9352aa2d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a5ca5b5d-dda9-4fa3-b398-548420aca8dd]
name                : eth23

_uuid               : 21b40cf8-6e19-4374-be4a-13d768e04daa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f27d8a20-2e0f-4b40-9629-a13d5f2147fd]
name                : eth21

_uuid               : fcd4ddc2-2c2b-4052-96b9-27b546e25654
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [22e3b26a-c21c-4349-a7ba-42550e63c917]
name                : br0

_uuid               : 9e21e1f7-f9d8-40f3-b899-093945f2b8e2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [51460f71-f8e4-4ba6-8147-652c195076a9]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f27d8a20-2e0f-4b40-9629-a13d5f2147fd
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
statistics          : {collisions=0, rx_bytes=3983437333, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=11296754, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a5ca5b5d-dda9-4fa3-b398-548420aca8dd
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4293714704, tx_dropped=0, tx_errors=0, tx_packets=5725788}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 51460f71-f8e4-4ba6-8147-652c195076a9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2926069362, tx_dropped=0, tx_errors=0, tx_packets=4832312}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 22e3b26a-c21c-4349-a7ba-42550e63c917
admin_state         : down
duplex              : full
ifindex             : 374
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
commit a48c85b2d672505b89e488d28066538705b94942
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Thu Jun 5 06:08:40 2014 +0000
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Thu Jun 5 13:21:50 2014 +1200

    revalidator: Use xcache when revalidation is required.
    
    One of the reasons that xlate_cache was introduced was to ensure that
    statistics were attributed to the correct rules and interfaces according
    to the flow that was installed into the datapath, rather than according
    to the current state of the flow table.
    
    This patch makes the revalidators use the xlate_cache to attribute stats
    when full revalidation is required, as the statistics belong to the old
    ruleset. However, when revalidating, the rules may have changed while
    leaving the datapath flows intact, so we still re-create the xcache at
    that point.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
