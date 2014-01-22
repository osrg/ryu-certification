---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
026acb5f-232c-452f-ab34-1c3152a6b209
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f5860bd4-aa01-45fc-8d1d-af705a475bf2
controller          : [a8f29895-ff80-4b23-9f27-6708b32f1a1a]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0b1d98e3-8cb3-4bae-8b0e-5f2cd555a0b8, 45d2eaf7-a947-4742-85de-f6c79f47a05c, 72873e36-d82c-4b4a-835e-b0daf40393c0]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a8f29895-ff80-4b23-9f27-6708b32f1a1a
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=312, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 72873e36-d82c-4b4a-835e-b0daf40393c0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [55ba8dfa-3331-4b50-a487-2b8b0437299a]
name                : eth7

_uuid               : 45d2eaf7-a947-4742-85de-f6c79f47a05c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6850655b-8bb6-4fc1-868f-e018992b231e]
name                : eth8

_uuid               : 0b1d98e3-8cb3-4bae-8b0e-5f2cd555a0b8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7fc22dfd-c16f-42d8-a873-77e4e4b28a5c]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7fc22dfd-c16f-42d8-a873-77e4e4b28a5c
admin_state         : up
duplex              : full
ifindex             : 131
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

_uuid               : 55ba8dfa-3331-4b50-a487-2b8b0437299a
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
statistics          : {collisions=0, rx_bytes=2336436780, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1589682, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 6850655b-8bb6-4fc1-868f-e018992b231e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1081396, tx_dropped=0, tx_errors=0, tx_packets=11620}
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
