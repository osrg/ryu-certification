---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
dad03b33-4549-4725-acf2-bd9027ac8827
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 20a06841-c03f-4f50-b4be-d069596d7fee
controller          : [53a03253-3c53-49d7-ab90-167a7e99ad83]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [3e81e791-1c28-49fb-834e-72b74fe04dd0, ae4169f3-7196-41c1-94a5-bf0451c64fe0, c1108c3b-7275-400b-b120-b3ba4b1d836d]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 53a03253-3c53-49d7-ab90-167a7e99ad83
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=296, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3e81e791-1c28-49fb-834e-72b74fe04dd0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3d99e21c-e8d3-49fe-bfb2-b5f7df950230]
name                : br0

_uuid               : ae4169f3-7196-41c1-94a5-bf0451c64fe0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [deb66ff0-be0c-49e2-bccd-db64baffaa74]
name                : eth7

_uuid               : c1108c3b-7275-400b-b120-b3ba4b1d836d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f5821240-7e23-4ef9-b28a-10a5a445605f]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : deb66ff0-be0c-49e2-bccd-db64baffaa74
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=3055774669, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72559432, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : f5821240-7e23-4ef9-b28a-10a5a445605f
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1423280, tx_dropped=0, tx_errors=0, tx_packets=15207}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 3d99e21c-e8d3-49fe-bfb2-b5f7df950230
admin_state         : up
duplex              : full
ifindex             : 200
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
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
commit a73fcd71115f3f17eacd07cad31e2cb055b0ba13
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Tue Feb 4 15:16:01 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Feb 7 08:40:50 2014 -0800

    ofproto: Update documentation
    
    'cls' is no longer a parameter to this function.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
