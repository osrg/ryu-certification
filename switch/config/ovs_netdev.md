---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a74596e2-589e-4251-939e-6c546c497f9a
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
_uuid               : e606fe18-a824-450b-85df-f7c21ff66244
controller          : [d2e5cdf9-3842-488d-808f-abd074eb1db5]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1507e583-3dac-4f7e-9b5f-7d80011e009a, bf838dcc-0338-4da6-af33-8d76b9325c84, f40aad67-ca48-44c2-a30a-f8f34c7d68ed]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d2e5cdf9-3842-488d-808f-abd074eb1db5
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=382, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : bf838dcc-0338-4da6-af33-8d76b9325c84
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2f4b5828-8000-4f06-ab72-cafbb5e07c6c]
name                : eth7

_uuid               : f40aad67-ca48-44c2-a30a-f8f34c7d68ed
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8c174002-a6d3-4841-a870-9594b4dccaa9]
name                : eth8

_uuid               : 1507e583-3dac-4f7e-9b5f-7d80011e009a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cf09c83b-f0ae-4a6a-a108-880449b81477]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2f4b5828-8000-4f06-ab72-cafbb5e07c6c
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
statistics          : {collisions=0, rx_bytes=3067762570, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72680891, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 8c174002-a6d3-4841-a870-9594b4dccaa9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5036830, tx_dropped=0, tx_errors=0, tx_packets=53704}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : cf09c83b-f0ae-4a6a-a108-880449b81477
admin_state         : up
duplex              : full
ifindex             : 676
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
commit ecb229bebb9dd2687848dcebc10d2556ae1f2a87
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Sun Mar 23 14:47:47 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Sun Mar 23 14:47:47 2014 -0700

    Disable OF1.4 in ovs-vswitchd and ovs-ofctl without specially enabling.
    
    When the OF1.4 is made safe, so that receiving an unimplemented message
    cannot crash the switch, this commit should be reverted.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
