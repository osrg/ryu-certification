---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7ed561cb-1097-4d2e-88a6-e2d150888797
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8a5f9068-6a61-44db-ac45-89dfc8c3a15f
controller          : [92daadb0-f067-47c1-918d-ac90b1c6c082]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [791bfbec-ffdc-47ce-b189-941d287e631a, b06fa94c-9cbb-4703-af3f-82db290f2dad, f489411a-60ef-4153-881f-94fe2c4b6641, f6cf8e25-bdf9-4b48-a5e7-c0c140086c10]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 92daadb0-f067-47c1-918d-ac90b1c6c082
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=687, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 791bfbec-ffdc-47ce-b189-941d287e631a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7d07b238-c5d1-4c79-95e2-28619a2d2541]
name                : eth22

_uuid               : b06fa94c-9cbb-4703-af3f-82db290f2dad
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [109f0fc5-ab85-45b2-b7fa-eeceaac47d51]
name                : br0

_uuid               : f6cf8e25-bdf9-4b48-a5e7-c0c140086c10
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5d59cf49-4901-48ad-9b30-5a479443de58]
name                : eth23

_uuid               : f489411a-60ef-4153-881f-94fe2c4b6641
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cd09ecaf-b1e6-4fdd-8060-4949a93cfecf]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7d07b238-c5d1-4c79-95e2-28619a2d2541
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=160726043572, tx_dropped=0, tx_errors=0, tx_packets=107200741}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 109f0fc5-ab85-45b2-b7fa-eeceaac47d51
admin_state         : down
duplex              : full
ifindex             : 323
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

_uuid               : 5d59cf49-4901-48ad-9b30-5a479443de58
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=14381734500, tx_dropped=0, tx_errors=0, tx_packets=9587823}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : cd09ecaf-b1e6-4fdd-8060-4949a93cfecf
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
statistics          : {collisions=0, rx_bytes=271104877507, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=180847527, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3ca3ce0c1fab6331ba9edced207f9fdfe0816602
Author:     Jean Tourrilhes &lt;jean.tourrilhes@hp.com&gt;
AuthorDate: Wed Oct 22 12:41:50 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Nov 4 11:23:49 2014 -0800

    tests: Make sure test for actset_output tests initial condition.
    
    ONF-JIRA: EXT-233
    Signed-off-by: Jean Tourrilhes &lt;jt@hpl.hp.com&gt;
</pre>
