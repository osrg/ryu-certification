---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ebe3b0d6-ad1a-412c-a112-03a5d66835b0
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 3b0b76f4-ef45-4c0d-a766-f7b9f859bb7a
controller          : [fb057667-c6e3-4192-9ad0-09ecb449ce62]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [06085fe3-cc3c-44a7-8dec-5e53c6b5aea2, 2a6454ec-da6e-4aba-8b96-d6a7394a14d3, f535b06c-7aa2-43fc-90f2-8aa6f790580b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : fb057667-c6e3-4192-9ad0-09ecb449ce62
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=937, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f535b06c-7aa2-43fc-90f2-8aa6f790580b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5a140287-89ff-41e2-9c0c-90e8eec8454c]
name                : br0

_uuid               : 2a6454ec-da6e-4aba-8b96-d6a7394a14d3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1ec1df7b-b65f-45ed-bdff-108d3be7ce59]
name                : eth7

_uuid               : 06085fe3-cc3c-44a7-8dec-5e53c6b5aea2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [efd929a8-5a11-4f1f-878b-f8f3f7d6ee45]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : efd929a8-5a11-4f1f-878b-f8f3f7d6ee45
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7119538, tx_dropped=0, tx_errors=0, tx_packets=75888}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 5a140287-89ff-41e2-9c0c-90e8eec8454c
admin_state         : down
duplex              : full
ifindex             : 940
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 1ec1df7b-b65f-45ed-bdff-108d3be7ce59
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
statistics          : {collisions=0, rx_bytes=3074764713, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72751961, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 65a0903b26bdff3e42dc0fa78ef5b73a48448e80
Author:     Thomas Graf &lt;tgraf@redhat.com&gt;
AuthorDate: Wed Apr 9 17:19:17 2014 +0200
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Apr 9 09:57:42 2014 -0700

    bridge: improve vlan mode related error messages when adding port
    
    Inform about fallback to trunk mode and convert errors to warnings
    when we are not failing.
    
    Signed-off-by: Thomas Graf &lt;tgraf@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
