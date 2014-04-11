---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c1880bcb-761e-4b67-8ead-e6444ff6bfec
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
_uuid               : 78553fe5-0172-4792-a4bc-3bd1a7acc160
controller          : [08f3bb3b-ef4a-41f4-80bb-80a7350801e0]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [386acb9b-89ed-4d66-8b52-34bbbe55d431, 746508eb-8751-41cd-87d0-de60aeaf4daa, 79795e53-04b6-4d18-b799-371aedeb80f2]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 08f3bb3b-ef4a-41f4-80bb-80a7350801e0
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=927, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 386acb9b-89ed-4d66-8b52-34bbbe55d431
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [edef4f25-a944-41a3-adb0-8f0922b26ec8]
name                : br0

_uuid               : 79795e53-04b6-4d18-b799-371aedeb80f2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e0bd7ee5-a174-4211-9775-7b3a6746222e]
name                : eth8

_uuid               : 746508eb-8751-41cd-87d0-de60aeaf4daa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9d2c7950-b4b0-45ee-92ce-872e8745c277]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9d2c7950-b4b0-45ee-92ce-872e8745c277
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
statistics          : {collisions=0, rx_bytes=3075668200, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72761163, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : e0bd7ee5-a174-4211-9775-7b3a6746222e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7380657, tx_dropped=0, tx_errors=0, tx_packets=78673}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : edef4f25-a944-41a3-adb0-8f0922b26ec8
admin_state         : down
duplex              : full
ifindex             : 980
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
commit f085ba1e8ade76aba2273303b601565b8c12fb8d
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Apr 11 10:39:20 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Apr 11 11:17:03 2014 -0700

    debian: Better document how to get a kernel module in README.Debian.
    
    This moves existing text from INSTALL.Debian into the README.Debian
    installed as part of the openvswitch-switch package, and adds a reference
    from the former to the latter.
    
    Reported-by: Brian Candler &lt;b.candler@pobox.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
