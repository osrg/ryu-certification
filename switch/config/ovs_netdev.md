---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
50300bd2-461c-49fa-913b-46be80b9ac25
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : dad60eb1-2a67-4118-a3d8-5aef12b87544
controller          : [c5afe4fc-5f56-49f3-90ff-223a3fad8044]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [6578535e-fcc8-4829-856b-c205aad9508d, 8fbd1826-ff82-4018-97ad-7bacece258ff, f5b3d52e-ad7e-4f98-9f2b-74d47b71aeb8]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c5afe4fc-5f56-49f3-90ff-223a3fad8044
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=297, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6578535e-fcc8-4829-856b-c205aad9508d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ef55f463-98b1-405d-80e8-cec179d97e37]
name                : br0

_uuid               : 8fbd1826-ff82-4018-97ad-7bacece258ff
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [baa75b90-2d8f-4647-9e98-fcec178b6b2e]
name                : eth8

_uuid               : f5b3d52e-ad7e-4f98-9f2b-74d47b71aeb8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6b697e1a-2e16-4a4a-80df-f621dbecedaa]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : baa75b90-2d8f-4647-9e98-fcec178b6b2e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=551280, tx_dropped=0, tx_errors=0, tx_packets=5940}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 6b697e1a-2e16-4a4a-80df-f621dbecedaa
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
statistics          : {collisions=0, rx_bytes=1762155, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=17820, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : ef55f463-98b1-405d-80e8-cec179d97e37
admin_state         : up
duplex              : full
ifindex             : 81
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
commit 6a4d3ab53d53bc97ab9eee8709c5720dea1fb260
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed Jan 15 10:22:20 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jan 16 12:27:03 2014 -0800

    ofproto-dpif: Add more lock annotations.
    
    This annotation would have caught the bug fixed by commit 491a67a0005347130
    (ofproto-dpif-xlate: Avoid recursive acquisition of xlate_rwlock.).
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    CC: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
</pre>
