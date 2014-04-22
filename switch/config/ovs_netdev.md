---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
211d3fa1-b53b-429d-95af-c208ca544940
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b9a8f3e8-7baf-4861-8644-8d37b638876a
controller          : [ecf61c00-6fe3-46fc-a713-ce4e5ea3a08d]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1a70d756-6de4-4d8d-91e8-dd30259eeb25, 4689e607-2024-4c90-9c28-6590afec6876, 46b9780d-037d-4eaf-9633-533f2cbb4911, f21f9ea4-ea22-4f6f-926a-4d1cf10c3e5e]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ecf61c00-6fe3-46fc-a713-ce4e5ea3a08d
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=572, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f21f9ea4-ea22-4f6f-926a-4d1cf10c3e5e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5972aadd-8136-4310-8a41-bf7c034149f8]
name                : eth21

_uuid               : 46b9780d-037d-4eaf-9633-533f2cbb4911
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1b773bb3-409a-41e8-9269-62f5f71819ca]
name                : eth23

_uuid               : 1a70d756-6de4-4d8d-91e8-dd30259eeb25
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [abe77a9d-e130-4413-a539-608c54f2ea76]
name                : eth22

_uuid               : 4689e607-2024-4c90-9c28-6590afec6876
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [37b181db-6edd-49da-9453-6bab79172359]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : abe77a9d-e130-4413-a539-608c54f2ea76
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1500
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=793269210, tx_dropped=0, tx_errors=0, tx_packets=533563}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 5972aadd-8136-4310-8a41-bf7c034149f8
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=1201247701, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=812055, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 1b773bb3-409a-41e8-9269-62f5f71819ca
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1500
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=540018000, tx_dropped=0, tx_errors=0, tx_packets=360012}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 37b181db-6edd-49da-9453-6bab79172359
admin_state         : down
duplex              : full
ifindex             : 1087
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
commit 0d21340a5a1e26bba46522ba4666033564f8e930
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Fri Apr 18 09:00:46 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Tue Apr 22 15:21:13 2014 -0700

    testsuite.at: Workaround for carriage returns on windows.
    
    In unit tests, we compare text written in logs or stdout/stderr
    to figure out the success or failure of tests. In Windows,
    since new line is represented by CR+LF, autoconf tests run in
    MinGW environment fail.
    
    Asking diff to ignore trailing carriage returns is one way
    to solve the problem
    
    Suggested-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
