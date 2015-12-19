---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
40513e24-1350-4b9c-ab1c-1df0c6c1c63f
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8e74a24a-8cdc-4e5c-a81d-9480dcfdd20e
controller          : [a02d0f1e-9f9f-4b83-820f-1eaa3cdf0f2f]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2a467fb0-18bb-4bad-becc-e650429ca741, 6e5fb821-362f-43f7-80b4-803e54e9f150, d52906b9-6429-41bc-9cd9-cb0470683a17, e9a20adc-6440-4648-b138-123c209b2682]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a02d0f1e-9f9f-4b83-820f-1eaa3cdf0f2f
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e9a20adc-6440-4648-b138-123c209b2682
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3c537bc1-0911-4cd0-90cb-59fd9dee4dd1]
name                : "eth22"

_uuid               : 2a467fb0-18bb-4bad-becc-e650429ca741
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b864e0e4-8dd6-4403-88b5-c09d42987c81]
name                : "eth21"

_uuid               : d52906b9-6429-41bc-9cd9-cb0470683a17
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9585f9b7-01f6-498d-b039-e90cc7135f0e]
name                : "eth23"

_uuid               : 6e5fb821-362f-43f7-80b4-803e54e9f150
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ec4671d9-f87b-4fbe-ad6a-43d3e0c43fc0]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b864e0e4-8dd6-4403-88b5-c09d42987c81
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=42981030549, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28707033, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 3c537bc1-0911-4cd0-90cb-59fd9dee4dd1
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29540552495, tx_dropped=0, tx_errors=0, tx_packets=19717525}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ec4671d9-f87b-4fbe-ad6a-43d3e0c43fc0
admin_state         : down
duplex              : full
ifindex             : 698
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : 9585f9b7-01f6-498d-b039-e90cc7135f0e
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6907437000, tx_dropped=0, tx_errors=0, tx_packets=4604958}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 482553cca80f018d705b93b846182067fd272cdd
Author:     Ben Pfaff &lt;blp@ovn.org&gt;
AuthorDate: Wed Dec 16 23:32:54 2015 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Fri Dec 18 21:58:57 2015 -0800

    tun-metadata: Fix memory leak in tun_metadata_add_entry&#40;&#41; corner case.
    
    Found by valgrind.
    
    Reported-by: William Tu &lt;u9012063@gmail.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
    Acked-by: Jesse Gross &lt;jesse@kernel.org&gt;
</pre>
