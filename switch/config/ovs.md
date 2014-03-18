---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ec597de2-5617-47c1-8868-4ace204366d1
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
_uuid               : 41ddc813-81c3-4a4f-be08-881cf06a8809
controller          : [c5dd7312-84de-4474-b1c9-27b362ab1274]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [c4749e9f-79a5-4559-8623-556cbb86b9ce, dcf12877-fd5c-4fac-a17f-983fd7211ff1, e19c5997-e270-4a87-b315-efa26f75955b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c5dd7312-84de-4474-b1c9-27b362ab1274
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : dcf12877-fd5c-4fac-a17f-983fd7211ff1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [321cb8f9-cfb3-4766-b92a-4ae5dca63ef4]
name                : eth7

_uuid               : e19c5997-e270-4a87-b315-efa26f75955b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [092f93cf-791e-4820-a0a8-9f15e4d6c906]
name                : eth8

_uuid               : c4749e9f-79a5-4559-8623-556cbb86b9ce
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a1fad3ff-38ca-4b89-8484-d5bcb39668d1]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 321cb8f9-cfb3-4766-b92a-4ae5dca63ef4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 092f93cf-791e-4820-a0a8-9f15e4d6c906
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : a1fad3ff-38ca-4b89-8484-d5bcb39668d1
admin_state         : up
ifindex             : 577
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
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
