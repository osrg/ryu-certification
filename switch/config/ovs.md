---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
97976b6d-dc79-4213-ac0c-6bfcd48c216d
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
_uuid               : 1901c9b7-3292-4829-91e8-b51c1f007f1c
controller          : [c2e36805-0598-4f00-afc4-2c27a4ebe180]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [35c37cb0-fbf7-4ecd-8157-13db9797fd51, b665014e-6e81-48bc-a5d0-05da9bebb855, f0879760-9449-4fda-9af8-78178b146314]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c2e36805-0598-4f00-afc4-2c27a4ebe180
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=356, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 35c37cb0-fbf7-4ecd-8157-13db9797fd51
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b172ffa8-a9dd-4537-a3c6-b930b4d348a9]
name                : br0

_uuid               : f0879760-9449-4fda-9af8-78178b146314
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1939b0a5-0775-4c37-9fa3-afeddd0cfa56]
name                : eth8

_uuid               : b665014e-6e81-48bc-a5d0-05da9bebb855
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c7d2ec05-c084-45e5-9466-ea3ffbc45305]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b172ffa8-a9dd-4537-a3c6-b930b4d348a9
admin_state         : up
ifindex             : 133
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 1939b0a5-0775-4c37-9fa3-afeddd0cfa56
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : c7d2ec05-c084-45e5-9466-ea3ffbc45305
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
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7849d3e4cab657eb42b513b0d9ad656fc38259bd
Author:     Ansis Atteka &lt;aatteka@nicira.com&gt;
AuthorDate: Mon Jan 20 17:16:39 2014 -0800
Commit:     Ansis Atteka &lt;aatteka@nicira.com&gt;
CommitDate: Tue Jan 21 17:12:16 2014 -0800

    ipsec: install iptables rules that set IPsec bit in skb mark
    
    Without these two iptables rules (one for UDP encapsulated IPsec and
    another for direct IPsec), ovs-vswitchd would incorrectly conclude
    that GRE packet belonged to a plain GRE tunnel instead of IPsec GRE
    tunnel.
    
    Reported-by: Aryan TaheriMonfared &lt;aryan.taherimonfared@uis.no&gt;
    Reported-by: Daniel Hiltgen &lt;daniel@netkine.com&gt;
    Signed-off-by: Ansis Atteka &lt;aatteka@nicira.com&gt;
</pre>
