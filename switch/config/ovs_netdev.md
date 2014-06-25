---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a00f7493-a805-420e-9e57-906b87143560
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 994406d2-b8f3-4c76-b772-8d77525491fe
controller          : [d7f4879a-b18b-466f-b2e8-270749c5123f]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [002f8985-9449-40e9-ac0d-62c4e881f4e7, 4e8abadc-9627-4991-b44b-c64b8d010f0e, 61ae6938-2e0a-4aea-8705-e74d1304dfb9, ed5d6846-86ed-450e-872b-fbc9a3852431]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d7f4879a-b18b-466f-b2e8-270749c5123f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=992, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4e8abadc-9627-4991-b44b-c64b8d010f0e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [de916eda-1e68-49bc-8940-776a5a4c0b68]
name                : br0

_uuid               : 61ae6938-2e0a-4aea-8705-e74d1304dfb9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d95513ea-e7fe-4223-b826-be69f49bfe6c]
name                : eth23

_uuid               : 002f8985-9449-40e9-ac0d-62c4e881f4e7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8f27bc32-1472-4e82-bbab-d947651e4f22]
name                : eth22

_uuid               : ed5d6846-86ed-450e-872b-fbc9a3852431
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [174edee0-b0a5-4fe1-9ffb-9c971ae02bce]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 174edee0-b0a5-4fe1-9ffb-9c971ae02bce
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
statistics          : {collisions=0, rx_bytes=2051859108, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=90256497, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8f27bc32-1472-4e82-bbab-d947651e4f22
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1729699868, tx_dropped=0, tx_errors=0, tx_packets=35561402}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d95513ea-e7fe-4223-b826-be69f49bfe6c
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=324965784, tx_dropped=0, tx_errors=0, tx_packets=11670574}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : de916eda-1e68-49bc-8940-776a5a4c0b68
admin_state         : down
duplex              : full
ifindex             : 668
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 2b651e449bb0005403e7a0474d56be2752567f4f
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Jun 24 16:39:33 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Jun 24 17:12:22 2014 -0700

    dpif: When executing actions needs help, use &quot;set&quot; action to set tunnel.
    
    Open vSwitch userspace is able to implement some actions that the kernel
    doesn't support, such as modifying ARP fields.  When it does this for a
    tunneled packet, it needs to supply the tunnel information with a &quot;set&quot;
    action, because the Linux kernel datapath throws away tunnel information
    supplied in the OVS_PACKET_CMD_EXECUTE metadata argument.
    
    VMware-BZ: #1270110
    Reported-by: Srinivas Neginhal &lt;sneginha@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
