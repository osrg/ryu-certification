---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3185536d-7010-4d8a-9a06-ee0db2a048fc
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
_uuid               : 50471713-40fc-4e9f-a99b-faabb55dbea2
controller          : [5c0b63b7-8a4a-4a85-86eb-f10468fad58f]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [260827a0-48de-4643-b750-a45fd11c18c9, 86659847-1d2e-4f3f-a89c-8c58af829a4e, c87270ea-5386-4a57-85c8-072449b339af]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5c0b63b7-8a4a-4a85-86eb-f10468fad58f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=377, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 260827a0-48de-4643-b750-a45fd11c18c9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7253ed53-79d5-4614-b961-b14112e8e2ae]
name                : eth7

_uuid               : c87270ea-5386-4a57-85c8-072449b339af
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f752cef4-ae96-4217-99a6-88fe340acc8d]
name                : br0

_uuid               : 86659847-1d2e-4f3f-a89c-8c58af829a4e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3cb434c8-2e13-470e-8b8d-6802dff75cd5]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f752cef4-ae96-4217-99a6-88fe340acc8d
admin_state         : up
duplex              : full
ifindex             : 721
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

_uuid               : 3cb434c8-2e13-470e-8b8d-6802dff75cd5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5422242, tx_dropped=0, tx_errors=0, tx_packets=57807}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 7253ed53-79d5-4614-b961-b14112e8e2ae
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
statistics          : {collisions=0, rx_bytes=3069058958, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72694046, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a0cbddc04b3a152812712bfbdcfb17119e80317d
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Wed Mar 26 05:13:43 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Mar 25 13:18:19 2014 -0700

    netdev-bsd: compilation fixes
    
    This fixes regressions from commit f7791740
    (netdev: Rename netdev_rx to netdev_rxq)
    and commit df1e5a3b.
    (netdev: Extend rx_recv to pass multiple packets.)
    
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
