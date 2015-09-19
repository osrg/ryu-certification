---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
047fa091-b6e3-4d68-b875-6b8ec73efd96
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : caca59bc-ace2-4ee2-8a6a-d8fcdd2549b2
controller          : [e1cbdf3c-ef20-4489-8206-7dc4e713db2c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [5fc348f7-b851-42cb-808b-bdaa95f5d062, 868b1934-adb3-4a37-8f6c-12e41c8fd0c2, cceb8b72-53d9-4ce5-859a-aafae84ac44f, e29c3205-813f-4e40-a776-93c4651450be]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e1cbdf3c-ef20-4489-8206-7dc4e713db2c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 868b1934-adb3-4a37-8f6c-12e41c8fd0c2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [333b4c73-236a-450e-acf8-cf8b397eb96e]
name                : "eth21"

_uuid               : e29c3205-813f-4e40-a776-93c4651450be
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b9fc5b47-2836-4ac2-b474-dabce28e23b0]
name                : "eth23"

_uuid               : cceb8b72-53d9-4ce5-859a-aafae84ac44f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8c807be4-d49e-49f0-a349-01b508ae87f9]
name                : "eth22"

_uuid               : 5fc348f7-b851-42cb-808b-bdaa95f5d062
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [03db5716-0217-4e29-80bb-616074606ebd]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8c807be4-d49e-49f0-a349-01b508ae87f9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18089315792, tx_dropped=0, tx_errors=0, tx_packets=12064077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 03db5716-0217-4e29-80bb-616074606ebd
admin_state         : down
duplex              : full
ifindex             : 477
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

_uuid               : b9fc5b47-2836-4ac2-b474-dabce28e23b0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1176922500, tx_dropped=0, tx_errors=0, tx_packets=784615}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 333b4c73-236a-450e-acf8-cf8b397eb96e
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
statistics          : {collisions=0, rx_bytes=24024581534, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16026376, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 449b81311336977d874f80adde9c275dc67e0f8c
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Fri Sep 18 17:47:37 2015 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Fri Sep 18 17:47:37 2015 -0700

    dpif-netdev: Exact match non-presence of vlans.
    
    The Netlink encoding of datapath flow keys cannot express wildcarding
    the presence of a VLAN tag. Instead, a missing VLAN tag is interpreted
    as exact match on the fact that there is no VLAN.  This makes reading
    datapath flow dumps confusing, since for everything else, a missing
    key value means that the corresponding key was wildcarded.
    
    Unless we refactor a lot of code that translates between Netlink and
    struct flow representations, we have to do the same in the userspace
    datapath.  This makes at least the flow install logs show that the
    vlan_tci field is matched to zero.  However, the datapath flow dumps
    remain as they were before, as they are performed using the netlink
    format.
    
    Add a test to verify that packet with a vlan will not match a rule
    that may seem wildcarding the presence of the vlan tag.  Applying this
    test without the userspace datapath modification showed that the
    userspace datapath failed to create a new datapath flow for the VLAN
    packet before this patch.
    
    Reported-by: Tony van der Peet &lt;tony.vanderpeet@gmail.com&gt;
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
