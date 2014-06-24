---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
13da735f-e013-4c02-8122-a787ecb7d50a
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0ee62c9d-4698-45c9-b5a1-b6c87ea527dc
controller          : [c5516d7f-64c9-4acc-b390-52dec2950c07]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [01664ece-ec17-41d8-9072-ce2621b72a7d, 4c347522-a168-4ea5-9e81-314969434128, 589e5d4e-781d-4b91-89e9-d018b007aaab, a420a1b0-bcfe-4973-90e8-004cd0bdf1ed]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c5516d7f-64c9-4acc-b390-52dec2950c07
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=977, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a420a1b0-bcfe-4973-90e8-004cd0bdf1ed
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0357d379-fa0e-485f-893a-84bc5bd45638]
name                : br0

_uuid               : 589e5d4e-781d-4b91-89e9-d018b007aaab
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b068fb98-3619-44b0-aa61-e78f3085f7ca]
name                : eth23

_uuid               : 01664ece-ec17-41d8-9072-ce2621b72a7d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fbe2d17e-309a-4267-b3b2-ed753b3e4496]
name                : eth22

_uuid               : 4c347522-a168-4ea5-9e81-314969434128
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [856ed705-63d2-494a-9c78-012251c6774e]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b068fb98-3619-44b0-aa61-e78f3085f7ca
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2944245580, tx_dropped=0, tx_errors=0, tx_packets=10553449}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0357d379-fa0e-485f-893a-84bc5bd45638
admin_state         : down
duplex              : full
ifindex             : 615
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

_uuid               : 856ed705-63d2-494a-9c78-012251c6774e
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
statistics          : {collisions=0, rx_bytes=1710055962, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=81427475, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : fbe2d17e-309a-4267-b3b2-ed753b3e4496
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3410952466, tx_dropped=0, tx_errors=0, tx_packets=33814793}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7b900689deb559599c535ef2c4cf72ff14bf54f9
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Mon Jun 16 11:29:29 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Jun 23 17:06:56 2014 -0700

    ofproto: Break out monitor deletion code
    
    Break out monitor deletion code into a new function
    flow_monitor_delete which is paramatised over the id of
    the monitor to delete.
    
    This is in preparation for supporting OpenFlow1.4 flow monitor requests
    with delete and modify commands.
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
