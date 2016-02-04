---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
177f999f-9642-458b-adfd-07412c6404cf
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e85beba3-7061-412b-8467-adb915278be8
controller          : [13f0c043-8590-46d2-b93c-4a2a277376a0]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2a2aa3f0-90ba-4b60-baf0-62800ec2437c, 680e4efe-145d-4ea4-96f6-dd0328b7b105, 771ccbe9-55ae-4099-8767-35f772172b25, ddae2000-4ea1-470f-a71a-154384d8bdd0]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 13f0c043-8590-46d2-b93c-4a2a277376a0
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2a2aa3f0-90ba-4b60-baf0-62800ec2437c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2a65d317-73b8-4893-b5d8-1a81f7767966]
name                : "eth23"

_uuid               : ddae2000-4ea1-470f-a71a-154384d8bdd0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b9da446b-c211-49c0-91e9-cd17149d73fb]
name                : "eth22"

_uuid               : 771ccbe9-55ae-4099-8767-35f772172b25
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6584b057-2209-4cb2-96ad-c06a383e30a4]
name                : "br0"

_uuid               : 680e4efe-145d-4ea4-96f6-dd0328b7b105
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b914e13f-c9b7-40e5-bd0e-ab674008c07c]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b9da446b-c211-49c0-91e9-cd17149d73fb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30435618006, tx_dropped=0, tx_errors=0, tx_packets=20319688}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 2a65d317-73b8-4893-b5d8-1a81f7767966
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=8398786500, tx_dropped=0, tx_errors=0, tx_packets=5599191}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b914e13f-c9b7-40e5-bd0e-ab674008c07c
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
statistics          : {collisions=0, rx_bytes=44970359696, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30044434, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 6584b057-2209-4cb2-96ad-c06a383e30a4
admin_state         : down
duplex              : full
ifindex             : 766
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
commit 9d2d2b5cd2421369d08422be8a349de974b53301
Author:     Joe Stringer &lt;joe@ovn.org&gt;
AuthorDate: Thu Dec 24 11:46:42 2015 -0800
Commit:     Joe Stringer &lt;joe@ovn.org&gt;
CommitDate: Thu Feb 4 10:32:03 2016 -0800

    travis: Update kernel matrix.
    
    Remove v4.2 as it is EOL; Add v4.3 as we support this version in
    OVS-2.5. Update other versions to the latest listed on kernel.org.
    
    Signed-off-by: Joe Stringer &lt;joe@ovn.org&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@ovn.org&gt;
</pre>
