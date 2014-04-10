---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
887a03a8-787c-411b-86ea-e1f8d72f3234
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c497e818-4a99-41cb-9e5a-8c2e502d9891
controller          : [4787ef78-d827-450d-ae1c-8c99bff7c91d]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [6ba4e467-c1f8-4f9b-8734-e345e9171f4f, 87a7be11-ab03-48cb-baeb-2dcb281264d5, b2fa506c-d039-4dc7-806b-7516500dec87]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4787ef78-d827-450d-ae1c-8c99bff7c91d
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=922, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b2fa506c-d039-4dc7-806b-7516500dec87
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [40e53bad-ee50-48d3-b60f-0e0bc5ce5b3c]
name                : br0

_uuid               : 87a7be11-ab03-48cb-baeb-2dcb281264d5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [670bea3b-7f22-4f68-9248-2162b2e2d1d8]
name                : eth7

_uuid               : 6ba4e467-c1f8-4f9b-8734-e345e9171f4f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f01fe5e7-17ec-46b3-b308-22e58a06863a]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 40e53bad-ee50-48d3-b60f-0e0bc5ce5b3c
admin_state         : down
duplex              : full
ifindex             : 950
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : f01fe5e7-17ec-46b3-b308-22e58a06863a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7190340, tx_dropped=0, tx_errors=0, tx_packets=76643}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 670bea3b-7f22-4f68-9248-2162b2e2d1d8
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
statistics          : {collisions=0, rx_bytes=3075010329, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72754462, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c2a77f33adec720dd0551361c44359710ff15a03
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Thu Apr 10 11:14:07 2014 +1200
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Apr 9 16:26:50 2014 -0700

    tests/ofproto-dpif: Use vlog to test dpif behaviour.
    
    Previously we made heavy use of the 'ovs-appctl dpif/dump-flows' command
    to verify that flows were being installed into the datapath correctly.
    However this is sensitive to timing, particularly when the behaviour of
    revalidator threads is modified. A common race condition involves flows
    being revalidated and deleted before the test script gets a chance to
    connect to ovs-vswitchd and dump the datapath flows.
    
    This patch reworks the tests to make use of the vlog facility for dpif,
    checking for flow installation and flow dump messages. Most tests are
    converted to check for flow installation, which should reduce these race
    conditions significantly. For tests that require packet counts, these
    will continue to check for flow_dump messages. Race conditions for these
    should be reduced but not eliminated.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
