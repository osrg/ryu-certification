---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
21e6c8f1-13d2-4904-9a3b-37c7280520a9
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
_uuid               : 6014e5d9-e5fb-451b-bdaf-81bf7e73fd4a
controller          : [f0b37ba2-c2b7-413d-bd5b-652eb1eb962a]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [06e8b8ae-1bd4-462c-9ea2-7f7cc17781a2, 0f0386de-4622-4c6a-958c-05a4e67ebf51, 73dcb58e-b342-4c1f-b16c-d6fd33bcec7b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f0b37ba2-c2b7-413d-bd5b-652eb1eb962a
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=937, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 06e8b8ae-1bd4-462c-9ea2-7f7cc17781a2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [769d82bf-1b7f-4acd-beaa-80325209dfea]
name                : br0

_uuid               : 0f0386de-4622-4c6a-958c-05a4e67ebf51
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [73f35434-62db-4c21-906f-2f1f3659f74c]
name                : eth7

_uuid               : 73dcb58e-b342-4c1f-b16c-d6fd33bcec7b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [13bcf525-3361-4a94-9dd5-4aa7a86198e2]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 73f35434-62db-4c21-906f-2f1f3659f74c
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
statistics          : {collisions=0, rx_bytes=3075257682, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72756982, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 13bcf525-3361-4a94-9dd5-4aa7a86198e2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7262049, tx_dropped=0, tx_errors=0, tx_packets=77408}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 769d82bf-1b7f-4acd-beaa-80325209dfea
admin_state         : down
duplex              : full
ifindex             : 962
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit bee83872cab0c76877de0d8d93847a03ddb10503
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Thu Apr 10 16:57:51 2014 +1200
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Apr 10 08:23:57 2014 -0700

    SubmittingPatches: Rename to CONTRIBUTING.
    
    This makes the GitHub interface aware of the contribution guidelines,
    so it will be displayed to contributors when they submit issues or pull
    requests.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
