---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
038cddc2-1c08-4ce1-81d9-a002e98a5d0c
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b238ea64-422c-4192-89e4-b6572de312c1
controller          : [19782352-242a-487f-9796-fed7a25276a6]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2890e4f5-ab69-45c9-bbdb-0a7f749e2a1c, 2c20c8b1-e427-46fa-b95f-a2cf9f3aef8e, 856479fe-c828-41e7-b650-7b59dc41278f, b2cab074-5519-4c8d-ad9c-b962233c8aa6]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 19782352-242a-487f-9796-fed7a25276a6
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=1062, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b2cab074-5519-4c8d-ad9c-b962233c8aa6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d2014cbe-052a-43b6-91ad-bf52a7c265d3]
name                : br0

_uuid               : 2890e4f5-ab69-45c9-bbdb-0a7f749e2a1c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6930cb06-040c-43e4-b8b8-6e9b43788b97]
name                : eth23

_uuid               : 2c20c8b1-e427-46fa-b95f-a2cf9f3aef8e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f7e69cfe-8cef-4870-97ab-9807991871d1]
name                : eth21

_uuid               : 856479fe-c828-41e7-b650-7b59dc41278f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [71aa639d-53b1-42db-bf17-11c336b9d298]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 71aa639d-53b1-42db-bf17-11c336b9d298
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2862318244, tx_dropped=0, tx_errors=0, tx_packets=1918828}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6930cb06-040c-43e4-b8b8-6e9b43788b97
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=812702204, tx_dropped=0, tx_errors=0, tx_packets=3405113}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d2014cbe-052a-43b6-91ad-bf52a7c265d3
admin_state         : down
duplex              : full
ifindex             : 242
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

_uuid               : f7e69cfe-8cef-4870-97ab-9807991871d1
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
statistics          : {collisions=0, rx_bytes=2764308434, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=4734608, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 84f0f298298465f9bd6f7e794b671587e4556503
Author:     Ryan Wilson &lt;wryan@nicira.com&gt;
AuthorDate: Tue May 27 17:34:14 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Tue May 27 17:41:19 2014 -0700

    ofproto-dpif-xlate: Implement RCU locking in ofproto-dpif-xlate.
    
    Before, a global read-write lock protected the ofproto-dpif
    / ofproto-dpif-xlate interface.  Handler and revalidator threads
    had to wait while configuration was being changed.  This patch
    implements RCU locking which allows handlers and revalidators
    to operate while configuration is being updated.
    
    Signed-off-by: Ryan Wilson &lt;wryan@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
