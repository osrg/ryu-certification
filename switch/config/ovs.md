---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4c9373aa-2f5d-4a48-8701-c581aa7dbaa6
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0d964560-f8e8-4ce1-abf0-ad64228471af
controller          : [b5ffc5cf-aeeb-48e5-8003-c3726bb65a6a]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [9208aef6-a565-46a1-8f06-472d15b782d5, 947b8a21-b34a-4e7b-9741-2348b2e19230, a191c746-e09b-473c-9ca7-1ac7327b83a0, be3a6037-25ce-4faf-8a18-8d4f42b8407d]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b5ffc5cf-aeeb-48e5-8003-c3726bb65a6a
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=681, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 947b8a21-b34a-4e7b-9741-2348b2e19230
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a92b3307-f3ae-4e90-9a49-a24a1a35ffd4]
name                : br0

_uuid               : a191c746-e09b-473c-9ca7-1ac7327b83a0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0e6e4789-1f23-4132-8064-5689e7750646]
name                : eth23

_uuid               : 9208aef6-a565-46a1-8f06-472d15b782d5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2ec701dd-2b44-405e-83a3-d98162925f7a]
name                : eth21

_uuid               : be3a6037-25ce-4faf-8a18-8d4f42b8407d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9df9fc1e-5fb1-4e3e-a56c-03de2db30987]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2ec701dd-2b44-405e-83a3-d98162925f7a
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
statistics          : {collisions=0, rx_bytes=1255945247, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=83897381, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0e6e4789-1f23-4132-8064-5689e7750646
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2002291500, tx_dropped=0, tx_errors=0, tx_packets=1334861}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9df9fc1e-5fb1-4e3e-a56c-03de2db30987
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=942996980, tx_dropped=0, tx_errors=0, tx_packets=49315330}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a92b3307-f3ae-4e90-9a49-a24a1a35ffd4
admin_state         : down
ifindex             : 63
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d9d8dbc80e955e39d326413ae3563c741e8611b8
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Tue Aug 5 23:30:31 2014 +0000
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Tue Aug 5 08:51:32 2014 -0700

    INSTALL.Windows: Update build instructions to do 'make'.
    
    We no-longer need to build individual targets on Windows. This information
    was lost when we committed the hyper-v changes to the repo.
    
    Resurrecting that information in this change.
    
    Also, added the testing instructions on how to setup a VLAN based network.
    
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
