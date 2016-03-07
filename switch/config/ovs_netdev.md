---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7196aa20-c45f-4667-8502-08d0fd66b150
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 2c759571-1398-4f35-bc42-154fea254b2d
controller          : [3ba45340-e728-4d47-988f-1e6e3edaca1a]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3a8c79a8-0617-4659-b565-c5fc24ff30c5, 76c972f7-8fb9-43cc-9311-17e822ff921a, 83045d3b-12a3-49e2-aedb-9eece549e699, dce0d166-01ba-4ab4-b7bf-b437e95b1eea]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3ba45340-e728-4d47-988f-1e6e3edaca1a
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="672", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3a8c79a8-0617-4659-b565-c5fc24ff30c5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a6743210-93f7-47ab-85df-98e2b601ddc0]
name                : "eth23"

_uuid               : dce0d166-01ba-4ab4-b7bf-b437e95b1eea
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9d86a16c-29b0-4c6f-81d1-7094cd04f9d0]
name                : "eth21"

_uuid               : 76c972f7-8fb9-43cc-9311-17e822ff921a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e5d25bf5-e397-4dfe-84f9-807ed73dfa3f]
name                : "eth22"

_uuid               : 83045d3b-12a3-49e2-aedb-9eece549e699
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9b5b2d65-2c9b-42c4-b224-430146facbfd]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9d86a16c-29b0-4c6f-81d1-7094cd04f9d0
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
statistics          : {collisions=0, rx_bytes=47895750213, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=32011135, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a6743210-93f7-47ab-85df-98e2b601ddc0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10590709500, tx_dropped=0, tx_errors=0, tx_packets=7060473}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : e5d25bf5-e397-4dfe-84f9-807ed73dfa3f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31753041323, tx_dropped=0, tx_errors=0, tx_packets=21205986}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9b5b2d65-2c9b-42c4-b224-430146facbfd
admin_state         : down
duplex              : full
ifindex             : 864
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
commit 674da62d386c17b84d88555cd57743e2a58aa766
Author:     Russell Bryant &lt;russell@ovn.org&gt;
AuthorDate: Mon Mar 7 10:23:35 2016 -0500
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Mon Mar 7 10:23:59 2016 -0500

    AUTHORS: Add Ramu Ramamurthy.
    
    Ramu is the author of 3a83007a76bbf05144cee1fda7ad81c1c717dca7.
    
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
</pre>
