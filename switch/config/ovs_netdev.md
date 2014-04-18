---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0f65a5d6-6337-423d-aea1-0e77c789ffbf
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
_uuid               : 501c8413-36ee-4997-8007-064289af1e0a
controller          : [06ebdb53-50ac-4980-bc56-40b2bddc98a7]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [07b6b2b3-1946-4e10-be36-b1c4a7937ac3, 1bd5727a-5e6d-487a-9d5e-2b12c3a5f348, 59766f3c-b8e8-4269-ac20-87ce2035f7b1]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 06ebdb53-50ac-4980-bc56-40b2bddc98a7
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=572, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 59766f3c-b8e8-4269-ac20-87ce2035f7b1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2389682c-7e9c-4805-9d44-490951e39b95]
name                : eth8

_uuid               : 1bd5727a-5e6d-487a-9d5e-2b12c3a5f348
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [26b5be25-1c0b-400f-a9b8-31a739f960a7]
name                : eth7

_uuid               : 07b6b2b3-1946-4e10-be36-b1c4a7937ac3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2a3ab2ea-b7ed-47d1-8692-eb8554ad41f2]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2389682c-7e9c-4805-9d44-490951e39b95
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7675888, tx_dropped=0, tx_errors=0, tx_packets=81823}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 26b5be25-1c0b-400f-a9b8-31a739f960a7
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
statistics          : {collisions=0, rx_bytes=3076457713, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72769643, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 2a3ab2ea-b7ed-47d1-8692-eb8554ad41f2
admin_state         : down
duplex              : full
ifindex             : 1024
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
commit b90de03449c0f285b73ce24e1b74c4887ebd3f97
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Thu Apr 17 17:16:34 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Fri Apr 18 14:01:05 2014 -0700

    dpif-linux: Add thread-safety annotations.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
