---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1e284863-1c65-4c4f-80cf-38a85f0e369d
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a3d2fde2-10c6-4b72-adfa-21f3362af603
controller          : [b20192b3-413e-40f5-b38d-1bd53caee4a0]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1bfc6dc9-4861-431a-b3fc-40dc038134ae, 7edbad3b-7e7f-4d3d-882c-002731cb2027, b6882b41-3d04-4ed1-b207-de8c70256d2e, dbda6749-376a-4a65-b744-fabafe88597b]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b20192b3-413e-40f5-b38d-1bd53caee4a0
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="16", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1bfc6dc9-4861-431a-b3fc-40dc038134ae
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7140d552-84ef-463d-a7b0-9a67e1ab8dec]
name                : "eth21"

_uuid               : dbda6749-376a-4a65-b744-fabafe88597b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a395e191-28b6-495a-93dc-7a23159a0d11]
name                : "br0"

_uuid               : b6882b41-3d04-4ed1-b207-de8c70256d2e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c22450df-1162-4dfd-857b-5271cc24c7a7]
name                : "eth23"

_uuid               : 7edbad3b-7e7f-4d3d-882c-002731cb2027
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3d6f7e5f-1105-42c0-8ef5-9fa27f14e16e]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a395e191-28b6-495a-93dc-7a23159a0d11
admin_state         : down
duplex              : full
ifindex             : 832
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

_uuid               : 7140d552-84ef-463d-a7b0-9a67e1ab8dec
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
statistics          : {collisions=0, rx_bytes=46959603085, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31381775, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 3d6f7e5f-1105-42c0-8ef5-9fa27f14e16e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31331263759, tx_dropped=0, tx_errors=0, tx_packets=20922235}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c22450df-1162-4dfd-857b-5271cc24c7a7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9889479000, tx_dropped=0, tx_errors=0, tx_packets=6592986}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 611099dc3017879efd9ccede68307e8a24c47894
Author:     RYAN D. MOATS &lt;rmoats@us.ibm.com&gt;
AuthorDate: Fri Feb 19 11:25:07 2016 -0600
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Thu Feb 25 13:00:07 2016 -0800

    Add useful information to ovn E2E test
    
    Make test 2002 &quot;ovn -- 3 HVs, 1 LS, 3 lports/HV&quot; output the OF flows from
    all three hypervisors to help in case something goes wrong.
    
    Signed-off-by: RYAN D. MOATS &lt;rmoats@us.ibm.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
