---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ab744c8f-c6e3-49f6-a3d3-069f0e4bede2
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 049a96f9-48a9-49b4-998f-f8d699ccf346
controller          : [dcd6126e-4eeb-4ae2-a19f-37e3276c9e39]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2f6791a4-e489-4b4b-836b-322517237f60, 39db7fa6-197b-4a9c-bc37-9d386f425507, 3c846618-a066-47d9-b76e-b8aea66ddf49, f6fefacc-7a25-4b2c-a5ae-8321582c1c1e]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : dcd6126e-4eeb-4ae2-a19f-37e3276c9e39
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=682, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2f6791a4-e489-4b4b-836b-322517237f60
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [20bc6775-4c99-47aa-8fd0-1d6feef15c3b]
name                : br0

_uuid               : 3c846618-a066-47d9-b76e-b8aea66ddf49
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [def3c7d2-5bdc-4f92-8af2-aee62ebf4a36]
name                : eth22

_uuid               : f6fefacc-7a25-4b2c-a5ae-8321582c1c1e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c96144ce-5173-4428-b607-2d9c5aea9758]
name                : eth21

_uuid               : 39db7fa6-197b-4a9c-bc37-9d386f425507
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [64462eca-de13-4e86-9731-b47c43495bbc]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 20bc6775-4c99-47aa-8fd0-1d6feef15c3b
admin_state         : down
duplex              : full
ifindex             : 95
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

_uuid               : 64462eca-de13-4e86-9731-b47c43495bbc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3590866500, tx_dropped=0, tx_errors=0, tx_packets=2393911}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c96144ce-5173-4428-b607-2d9c5aea9758
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
statistics          : {collisions=0, rx_bytes=3125741575, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=85154011, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : def3c7d2-5bdc-4f92-8af2-aee62ebf4a36
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1597992216, tx_dropped=0, tx_errors=0, tx_packets=49756680}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e16138e224014922e478b4789359b1746858d1f9
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Thu Aug 7 15:46:19 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Fri Aug 8 13:31:08 2014 -0700

    datapath: Optimize recirc action.
    
    OVS need to flow key for flow lookup in recic action. OVS
    does key extract in recic action. Most of cases we could
    use OVS_CB packet key directly and can avoid packet flow key
    extract. SET action we can update flow-key along with packet
    to keep it consistent. But there are some action like MPLS
    pop which forces OVS to do flow-extract. In such cases we
    can mark flow key as invalid so that subsequent recirc
    action can do full flow extract.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
