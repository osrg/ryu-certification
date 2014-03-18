---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9c729949-8671-449d-ab97-0e6f1ff0a07b
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
_uuid               : 78d94ea9-c0f6-42d2-8f39-95174f017fef
controller          : [6125ab54-1b4f-4e5b-a18f-3d51eef6740c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [00a6a539-49f9-414a-b65c-bc3113cec754, 13a41c1b-d6e3-4ca0-a74e-f6293ab5fa81, 72a55756-e573-42f9-8e09-4aa718175bfa]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6125ab54-1b4f-4e5b-a18f-3d51eef6740c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 00a6a539-49f9-414a-b65c-bc3113cec754
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d61532af-f8c7-4616-88c4-76e325a744d2]
name                : br0

_uuid               : 72a55756-e573-42f9-8e09-4aa718175bfa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [869850be-4f3a-4f60-ba21-e3c753e8091d]
name                : eth8

_uuid               : 13a41c1b-d6e3-4ca0-a74e-f6293ab5fa81
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aabf6d8b-dab8-408c-85af-1d2221b5fa58]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 869850be-4f3a-4f60-ba21-e3c753e8091d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4363182, tx_dropped=0, tx_errors=0, tx_packets=46530}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : aabf6d8b-dab8-408c-85af-1d2221b5fa58
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
statistics          : {collisions=0, rx_bytes=3065453892, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72657451, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : d61532af-f8c7-4616-88c4-76e325a744d2
admin_state         : up
duplex              : full
ifindex             : 575
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
commit e935fc32fa0d346b0205dcd4e97859c76caab3d0
Author:     Arun Sharma &lt;arun.sharma@calsoftinc.com&gt;
AuthorDate: Tue Mar 18 17:44:42 2014 +0530
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Mar 18 08:24:22 2014 -0700

    Man ovs-ofctl: Typo in arp_spa &amp; arp_tpa
    
    It seems there is a typo in definition of arp_spa &amp; arp_tpa
    
    Signed-off-by: Arun Sharma &lt;arun.sharma@calsoftinc.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
