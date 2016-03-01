---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d54da894-8c8d-40c2-956c-2d0cade9cd79
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0bd65429-6358-44ba-9850-eeced9dcd9f7
controller          : [d93eac2f-2931-4b12-bcaf-606462996b0e]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [41e98d97-2c8b-4c4b-b815-0d9663dc9ec8, 720e5293-9650-4b14-b1b8-7865a23afa75, ad74bc1d-6069-49ef-93c7-140144621cc3, b6730b39-735f-4561-a9e5-fffc806c66a9]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d93eac2f-2931-4b12-bcaf-606462996b0e
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="672", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b6730b39-735f-4561-a9e5-fffc806c66a9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ad6e840a-3315-437d-ab83-647d99486fd9]
name                : "eth23"

_uuid               : ad74bc1d-6069-49ef-93c7-140144621cc3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bf4b0a38-0e60-4502-a3fe-3caa487de271]
name                : "eth22"

_uuid               : 41e98d97-2c8b-4c4b-b815-0d9663dc9ec8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [77a4ec51-1e3c-46f5-9e08-9fca55288386]
name                : "eth21"

_uuid               : 720e5293-9650-4b14-b1b8-7865a23afa75
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f4a804be-931f-490a-9824-12b77554aac5]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : bf4b0a38-0e60-4502-a3fe-3caa487de271
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31542354291, tx_dropped=0, tx_errors=0, tx_packets=21064245}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 77a4ec51-1e3c-46f5-9e08-9fca55288386
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
statistics          : {collisions=0, rx_bytes=47427673649, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31696453, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f4a804be-931f-490a-9824-12b77554aac5
admin_state         : down
duplex              : full
ifindex             : 848
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

_uuid               : ad6e840a-3315-437d-ab83-647d99486fd9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10239885000, tx_dropped=0, tx_errors=0, tx_packets=6826590}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d0a46cb4608e632f5028034762f0adde2ce947a0
Author:     Russell Bryant &lt;russell@ovn.org&gt;
AuthorDate: Mon Feb 29 15:51:57 2016 -0500
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Tue Mar 1 11:55:00 2016 -0500

    ofpbuf: Fix trivial spelling typo.
    
    s/bofy/body/. I noticed this spelling typo while reading this header
    file.
    
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
