---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8d302e29-a08d-4b76-8347-1f5c90afb87c
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c744427c-3ce8-4a52-928e-93c2f95a4852
controller          : [76439a33-025e-416e-b8ff-0c61e766ff68]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [05f2fe4e-c31d-417a-87ef-2b60cc093d31, 927b4296-e98a-43c0-b163-296e5e7baad0, b68a3621-bfd5-415d-8264-8c1eda686299, bbd11f83-f10f-4554-b094-fa01937cdf31]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 76439a33-025e-416e-b8ff-0c61e766ff68
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=961, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b68a3621-bfd5-415d-8264-8c1eda686299
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c1ab50da-1d9f-4040-a4f5-a4de8bda4ee7]
name                : eth21

_uuid               : 927b4296-e98a-43c0-b163-296e5e7baad0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [57427f91-a30d-49f2-84eb-9debf0999531]
name                : eth22

_uuid               : 05f2fe4e-c31d-417a-87ef-2b60cc093d31
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b078682e-fa5a-41b6-835e-02ab4b182356]
name                : eth23

_uuid               : bbd11f83-f10f-4554-b094-fa01937cdf31
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6eeda1a5-e92c-4778-a5c5-2f5a68c512c3]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 57427f91-a30d-49f2-84eb-9debf0999531
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2149023954, tx_dropped=0, tx_errors=0, tx_packets=12914305}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6eeda1a5-e92c-4778-a5c5-2f5a68c512c3
admin_state         : down
duplex              : full
ifindex             : 480
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

_uuid               : b078682e-fa5a-41b6-835e-02ab4b182356
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2958005908, tx_dropped=0, tx_errors=0, tx_packets=7698627}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c1ab50da-1d9f-4040-a4f5-a4de8bda4ee7
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
statistics          : {collisions=0, rx_bytes=2431233593, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27467154, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9a621f8274178f18d1ab8be7bc7db661c1f70104
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Thu Jun 12 13:19:25 2014 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Thu Jun 12 17:04:12 2014 -0700

    datapath:  avoid memory corruption in queue_userspace_packet&#40;&#41;
    
    In queue_userspace_packet&#40;&#41;, the ovs_nla_put_flow return value is
    not checked. This is fine as long as key_attr_size&#40;&#41; returns the
    correct value. In case it does not, the current code may corrupt buffer
    memory. Add a run time assertion catch this case to avoid silent
    failure.
    
    Reported-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
