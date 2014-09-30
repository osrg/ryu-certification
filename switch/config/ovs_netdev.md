---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e7b5e937-8336-4053-a915-c9db0299a473
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d72aae8e-788b-45e8-a8e7-4fe8429de988
controller          : [e7ccea67-5569-4ce3-bdfd-1c61cb876565]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [15dc5ba0-2b70-4518-b86d-8db04e669418, 347568ae-2233-4cb5-82a8-57f98d90e0c2, b46e018f-cfdd-4bbe-96a5-e80ca28ef72a, e907de92-7816-472e-b438-7d43b5505f97]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e7ccea67-5569-4ce3-bdfd-1c61cb876565
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=667, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 15dc5ba0-2b70-4518-b86d-8db04e669418
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2a8b92d9-27f2-499b-a148-1db50889428f]
name                : eth22

_uuid               : 347568ae-2233-4cb5-82a8-57f98d90e0c2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ec7529c9-0432-4c13-a920-9b15c77ac36b]
name                : eth23

_uuid               : e907de92-7816-472e-b438-7d43b5505f97
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [07d399f8-515c-489b-bcf2-276629f497de]
name                : br0

_uuid               : b46e018f-cfdd-4bbe-96a5-e80ca28ef72a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [75d42ef5-9461-41fb-95f7-8fea951679b0]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 07d399f8-515c-489b-bcf2-276629f497de
admin_state         : down
duplex              : full
ifindex             : 188
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

_uuid               : 2a8b92d9-27f2-499b-a148-1db50889428f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2939627502, tx_dropped=0, tx_errors=0, tx_packets=47799170}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ec7529c9-0432-4c13-a920-9b15c77ac36b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3553565204, tx_dropped=0, tx_errors=0, tx_packets=5232355}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 75d42ef5-9461-41fb-95f7-8fea951679b0
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
statistics          : {collisions=0, rx_bytes=1659879897, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=75610991, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 29058c4e16762a6e797612573b1675b1c499a943
Author:     Lilijun &lt;jerry.lilijun@huawei.com&gt;
AuthorDate: Tue Sep 30 16:55:25 2014 +0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Sep 30 08:39:39 2014 -0700

    pstream-unix: Increase listen count to 64 in punix_open&#40;&#41;.
    
    In my test with openstack setup, ovs-ofctl executes failed when there are
    many flow rules to be added by multiple threads.
    The error like this:
    ovs-ofctl: /var/run/openvswitch/br1.mgmt: failed to open socket &#40;Protocol
    error&#41;
    
    In the function listen&#40;fd, 10&#41; in punix_open&#40;&#41;, the number 10 should be
    modified to more bigger, such as 64 maybe a proper value.
    
    Signed-off-by: Lilijun &lt;jerry.lilijun@huawei.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
