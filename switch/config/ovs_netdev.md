---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
33b42ad9-38bb-4cb5-84bb-4f57654633c7
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : bf5f5429-60b6-453e-bdd2-c7a90458764a
controller          : [73430021-a641-450e-8ce5-b252036da223]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1d6a41ef-1440-4ce3-8859-33ccf1bfb039, 7bc242b6-1c2f-418a-bc07-4500c7e1578b, 8c7e3108-db6e-4b69-b933-d6f32be6f771, 9a74129f-95b6-4e3b-af86-68f4fa1d382e]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 73430021-a641-450e-8ce5-b252036da223
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=682, sec_since_disconnect=6, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8c7e3108-db6e-4b69-b933-d6f32be6f771
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [48f86079-e079-4cca-9665-e9e24dcb0444]
name                : br0

_uuid               : 7bc242b6-1c2f-418a-bc07-4500c7e1578b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3331b8e3-b62a-4084-bb1b-e3fe363901e4]
name                : eth21

_uuid               : 1d6a41ef-1440-4ce3-8859-33ccf1bfb039
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9ee71521-d5f9-46b9-bd69-6b532ccbc3eb]
name                : eth23

_uuid               : 9a74129f-95b6-4e3b-af86-68f4fa1d382e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cd7bb3c2-61ae-41f4-ad2f-ef6dcf4e5cde]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9ee71521-d5f9-46b9-bd69-6b532ccbc3eb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1041085408, tx_dropped=0, tx_errors=0, tx_packets=6420680}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 48f86079-e079-4cca-9665-e9e24dcb0444
admin_state         : down
duplex              : full
ifindex             : 223
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

_uuid               : cd7bb3c2-61ae-41f4-ad2f-ef6dcf4e5cde
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1720391444, tx_dropped=0, tx_errors=0, tx_packets=72763121}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3331b8e3-b62a-4084-bb1b-e3fe363901e4
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
statistics          : {collisions=0, rx_bytes=525688947, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=123547179, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5aca3322a1597575892d52188612f3b89860020b
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Thu Oct 9 08:23:37 2014 +0000
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Thu Oct 9 09:27:53 2014 -0700

    ovs-vswitchd: Fix high cpu utilization when acquire idl lock fails.
    
    When ovs-vswitchd fails to acquire the ovsdb idl lock &#40;either due to
    contention or due to invalid database path&#41;, ovs-vswitchd will spin
    on the global connectivity sequence number and consume 100% cpu.
    This is in that the local copy is different to the global sequence
    number and never updated when ovsdb idl is not locked.
    
    To fix this issue, this commit makes ovs-vswitchd not checking the
    global connectivity sequence number in that situation.
    
    Reported-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
