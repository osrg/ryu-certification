---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8f9736b4-d88f-4ed4-ae44-c1f4cc4aed92
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b7a77475-c71b-46b8-be3f-c47f25e79528
controller          : [230b4903-3c6a-4390-965e-b16b24e7de2f]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1078f90d-1fbc-476e-8687-e8d4d9bf7748, 45e6af9b-7c35-4f26-b610-0d998b0072f3, 79ab42f4-b3a6-4a3f-b5fe-9e70ee8ff081, a9f7c03d-04ba-4fad-8441-f58afb9acd6c]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 230b4903-3c6a-4390-965e-b16b24e7de2f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=967, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 79ab42f4-b3a6-4a3f-b5fe-9e70ee8ff081
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8537fe1a-0086-4178-8c16-3831c54f1c3e]
name                : eth21

_uuid               : 1078f90d-1fbc-476e-8687-e8d4d9bf7748
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [30f87e01-6942-4409-b697-b6aeaff15928]
name                : eth23

_uuid               : a9f7c03d-04ba-4fad-8441-f58afb9acd6c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1f8dab1e-8db3-4d42-8919-32304f44bd26]
name                : eth22

_uuid               : 45e6af9b-7c35-4f26-b610-0d998b0072f3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [295dd806-3238-4f44-8f2a-46fa576d3064]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 30f87e01-6942-4409-b697-b6aeaff15928
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1019417908, tx_dropped=0, tx_errors=0, tx_packets=6406235}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8537fe1a-0086-4178-8c16-3831c54f1c3e
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
statistics          : {collisions=0, rx_bytes=4139285697, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=25727926, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 1f8dab1e-8db3-4d42-8919-32304f44bd26
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1041507578, tx_dropped=0, tx_errors=0, tx_packets=12170037}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 295dd806-3238-4f44-8f2a-46fa576d3064
admin_state         : down
duplex              : full
ifindex             : 408
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 059ef3c65f596f93e56c7062e35977d429faa4ab
Author:     Ethan Jackson &lt;ethan@nicira.com&gt;
AuthorDate: Fri May 23 11:16:35 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Jun 6 15:32:23 2014 -0700

    ofproto: Destroy rule in ofproto_get_vlan_usage&#40;&#41;.
    
    Found by inspection.
    
    Signed-off-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Flavio Leitner &lt;fbl@redhat.com&gt;
</pre>
