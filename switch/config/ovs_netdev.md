---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d3250f89-ba62-4f8f-a273-7159a2bba951
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 6cd7dab7-5f8f-460a-bd14-89447df0ff22
controller          : [e99fd6be-e2a6-4462-8b1f-df0e8979282d]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1a350756-f561-494a-a551-1e1193372119, 45be16fc-bbc9-4555-9fbe-f091ae662354, 5b5bb471-44a8-4ff1-94d2-3c9a97a36d51, e1fff531-ad7c-4f7c-a8fa-e6785007a1e3]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e99fd6be-e2a6-4462-8b1f-df0e8979282d
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=571, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 45be16fc-bbc9-4555-9fbe-f091ae662354
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [deec706a-b4ea-4b83-a047-35d3222fd790]
name                : eth22

_uuid               : e1fff531-ad7c-4f7c-a8fa-e6785007a1e3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [60bc9242-5774-41b4-a4e2-5f15e3c64540]
name                : br0

_uuid               : 5b5bb471-44a8-4ff1-94d2-3c9a97a36d51
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e1dd6154-5590-40dd-94f4-96fcf9d153e6]
name                : eth21

_uuid               : 1a350756-f561-494a-a551-1e1193372119
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ace95a11-94e1-4d3d-a54e-3e73a2d26fbe]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e1dd6154-5590-40dd-94f4-96fcf9d153e6
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=1388286003, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=937373, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ace95a11-94e1-4d3d-a54e-3e73a2d26fbe
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1500
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=642295500, tx_dropped=0, tx_errors=0, tx_packets=428197}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 60bc9242-5774-41b4-a4e2-5f15e3c64540
admin_state         : down
duplex              : full
ifindex             : 1093
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

_uuid               : deec706a-b4ea-4b83-a047-35d3222fd790
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1500
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=901389448, tx_dropped=0, tx_errors=0, tx_packets=605870}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 84f7a5273bc627df61c9d71f4ce9f1f058c18545
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Apr 22 16:26:05 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Apr 22 16:28:16 2014 -0700

    TODO: Add the project list from the hackathon.
    
    I've had a couple of requests for an updated project list, so this commit
    adds it to the tree.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
