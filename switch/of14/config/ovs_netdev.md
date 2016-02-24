---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3003a9f8-3b37-4380-8a11-66db2384db06
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b69c649b-0586-47bb-8d75-43355fd79193
controller          : [0c666db2-3e4d-4ddc-978c-ba228c4c6f14]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1c25c1e3-a240-4a16-a1f4-31f14af65f1b, 61b6d24d-f65a-4c66-837a-6d7bd9dc73b0, 954b7151-147e-4a78-8913-a9c25aa4a550, e220510c-c7e6-47a7-89bc-3a423fb9f68f]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0c666db2-3e4d-4ddc-978c-ba228c4c6f14
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="11", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e220510c-c7e6-47a7-89bc-3a423fb9f68f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [acf14e5a-4514-4253-af43-6ff4b4fb56e3]
name                : "eth22"

_uuid               : 61b6d24d-f65a-4c66-837a-6d7bd9dc73b0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [10846b88-abf7-4a0d-866d-d627554b24ec]
name                : "eth23"

_uuid               : 954b7151-147e-4a78-8913-a9c25aa4a550
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5611f3e1-c012-4659-a9fd-ad68954111df]
name                : "eth21"

_uuid               : 1c25c1e3-a240-4a16-a1f4-31f14af65f1b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e9023cbc-99d1-4114-800d-a2ffa068e729]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 10846b88-abf7-4a0d-866d-d627554b24ec
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9801657000, tx_dropped=0, tx_errors=0, tx_packets=6534438}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : e9023cbc-99d1-4114-800d-a2ffa068e729
admin_state         : down
duplex              : full
ifindex             : 828
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

_uuid               : 5611f3e1-c012-4659-a9fd-ad68954111df
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
statistics          : {collisions=0, rx_bytes=46842581694, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31303103, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : acf14e5a-4514-4253-af43-6ff4b4fb56e3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31278706376, tx_dropped=0, tx_errors=0, tx_packets=20886876}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6c6eedc5d6730835a0d9724e2e8cfe9cdf03b07d
Author:     Saloni Jain &lt;saloni.jain@tcs.com&gt;
AuthorDate: Thu Feb 18 15:54:26 2016 +0530
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Wed Feb 24 10:55:07 2016 -0800

    Implement OFPT_TABLE_STATUS Message.
    
    On change in a table state, the controller needs to be informed with
    the OFPT_TABLE_STATUS message. The message is sent with reason
    OFPTR_VACANCY_DOWN or OFPTR_VACANCY_UP in case of change in remaining
    space eventually crossing any one of the threshold.
    
    Signed-off-by: Saloni Jain &lt;saloni.jain@tcs.com&gt;
    Co-authored-by: Rishi Bamba &lt;rishi.bamba@tcs.com&gt;
    Signed-off-by: Rishi Bamba &lt;rishi.bamba@tcs.com&gt;
    [blp@ovn.org added vacancy event initialization and tests
     and updated NEWS]
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
