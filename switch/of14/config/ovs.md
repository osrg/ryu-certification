---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6d422e9e-d54f-49d7-ac41-3296b92f92c2
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c29368dd-2f3e-43c9-9533-12fa135935c5
controller          : [b3b0418e-0d53-4c1c-b49d-76b687d812c0]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5ac1ff43-3603-4e92-8ea7-4b9168bdc46f, 5b25da81-f756-4098-ad31-72b584c69da2, 60da6450-b501-4f8a-8700-195258895ba6, cdd673c2-91d6-4e0c-a4ad-2edd770f9d8c]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b3b0418e-0d53-4c1c-b49d-76b687d812c0
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=977, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 60da6450-b501-4f8a-8700-195258895ba6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a3b57d61-be93-4748-bbc3-7351d3a874c4]
name                : br0

_uuid               : 5b25da81-f756-4098-ad31-72b584c69da2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [beab1ac0-d53f-4d67-8596-1156115456b3]
name                : eth23

_uuid               : cdd673c2-91d6-4e0c-a4ad-2edd770f9d8c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [00da1786-c3af-4c63-a5ab-50c31497131d]
name                : eth22

_uuid               : 5ac1ff43-3603-4e92-8ea7-4b9168bdc46f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [733485a3-36f4-41f0-a37d-080d90f135f7]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : beab1ac0-d53f-4d67-8596-1156115456b3
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=4123473580, tx_dropped=0, tx_errors=0, tx_packets=11339601}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a3b57d61-be93-4748-bbc3-7351d3a874c4
admin_state         : down
ifindex             : 658
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 00da1786-c3af-4c63-a5ab-50c31497131d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1524828198, tx_dropped=0, tx_errors=0, tx_packets=35423662}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 733485a3-36f4-41f0-a37d-080d90f135f7
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
statistics          : {collisions=0, rx_bytes=1467321628, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=89863652, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ccf4378615e93618e6ab8423fa1400b40876df91
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Tue Jun 24 20:56:57 2014 +0900
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Tue Jun 24 16:02:02 2014 -0700

    datapath: Add basic MPLS support to kernel
    
    Allow datapath to recognize and extract MPLS labels into flow keys
    and execute actions which push, pop, and set labels on packets.
    
    Based heavily on work by Leo Alterman, Ravi K, Isaku Yamahata and Joe Stringer.
    
    Cc: Ravi K &lt;rkerur@gmail.com&gt;
    Cc: Leo Alterman &lt;lalterman@nicira.com&gt;
    Cc: Isaku Yamahata &lt;yamahata@valinux.co.jp&gt;
    Cc: Joe Stringer &lt;joe@wand.net.nz&gt;
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
