---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
069febb5-5ee1-457c-8ec3-c739fa829601
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 9c053e05-122c-4515-98a8-d48448345c1f
controller          : [a7d917c2-ff57-4753-bbce-f3e23e7d0a2b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3dcf94e8-6d49-44e7-a1b2-6886a64c3c8b, 58be0bed-78c2-420e-a8e4-884766a0fea1, b937fff3-bc2f-4280-ac43-bc692b9dc7a3, b94b2fab-2fba-48eb-9fee-c03aab71e43c]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a7d917c2-ff57-4753-bbce-f3e23e7d0a2b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3dcf94e8-6d49-44e7-a1b2-6886a64c3c8b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [009b209d-b124-4f10-9d20-48c9e748a4fb]
name                : "eth22"

_uuid               : 58be0bed-78c2-420e-a8e4-884766a0fea1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8d8b3f84-9e8b-4441-ae9e-ac36565214ef]
name                : "eth23"

_uuid               : b94b2fab-2fba-48eb-9fee-c03aab71e43c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5260ae04-6a5d-41bf-b870-ae009bcf3a8d]
name                : "eth21"

_uuid               : b937fff3-bc2f-4280-ac43-bc692b9dc7a3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [20a67d6f-a909-4f62-9f52-d25d257aacf8]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 5260ae04-6a5d-41bf-b870-ae009bcf3a8d
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
statistics          : {collisions=0, rx_bytes=45789465933, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30595109, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 8d8b3f84-9e8b-4441-ae9e-ac36565214ef
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9012502500, tx_dropped=0, tx_errors=0, tx_packets=6008335}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 009b209d-b124-4f10-9d20-48c9e748a4fb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30804520187, tx_dropped=0, tx_errors=0, tx_packets=20567868}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 20a67d6f-a909-4f62-9f52-d25d257aacf8
admin_state         : down
duplex              : full
ifindex             : 794
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d5579e480863ed07402d400877cf37e701419b9e
Author:     Andy Zhou &lt;azhou@ovn.org&gt;
AuthorDate: Fri Feb 12 10:36:51 2016 -0800
Commit:     Andy Zhou &lt;azhou@ovn.org&gt;
CommitDate: Fri Feb 12 12:39:07 2016 -0800

    lib: Remove unused function prototypes
    
    Found by inspection.
    
    Signed-off-by: Andy Zhou &lt;azhou@ovn.org&gt;
    Acked-by: Russell Bryant &lt;russell@ovn.org&gt;
</pre>
