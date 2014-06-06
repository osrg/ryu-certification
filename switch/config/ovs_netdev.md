---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3df6e226-0a56-445f-98b1-f88d879e75b2
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8d2b5783-27aa-4a65-a52f-e2e88e80b1a2
controller          : [daf78dfc-861b-42e7-acbb-6ea5a3c32f4a]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5101c860-2736-435e-981f-12303636c4a0, 958ac196-e4be-409d-ab49-bafd3cee8741, b58fe5eb-e724-46c7-bc9a-041ab40f4d31, e27a73e8-869f-4516-9bb1-78228484994a]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : daf78dfc-861b-42e7-acbb-6ea5a3c32f4a
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=962, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e27a73e8-869f-4516-9bb1-78228484994a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7bb10788-64e7-4658-96ae-15bc32086ed1]
name                : br0

_uuid               : 5101c860-2736-435e-981f-12303636c4a0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ac248ad9-8095-42e6-926e-7ca6321bad7e]
name                : eth21

_uuid               : 958ac196-e4be-409d-ab49-bafd3cee8741
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7e058cec-d1d2-4e68-a2f8-56ab011d1d18]
name                : eth23

_uuid               : b58fe5eb-e724-46c7-bc9a-041ab40f4d31
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [769fdde6-6e1c-4323-bd45-ac2248eba92b]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7e058cec-d1d2-4e68-a2f8-56ab011d1d18
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=773843908, tx_dropped=0, tx_errors=0, tx_packets=6242519}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 7bb10788-64e7-4658-96ae-15bc32086ed1
admin_state         : down
duplex              : full
ifindex             : 398
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

_uuid               : ac248ad9-8095-42e6-926e-7ca6321bad7e
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
statistics          : {collisions=0, rx_bytes=1465414494, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=23942713, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 769fdde6-6e1c-4323-bd45-ac2248eba92b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3923798876, tx_dropped=0, tx_errors=0, tx_packets=11227325}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit efa085312b6d5b81718ac5cfe467f3aa36de8f25
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Wed May 14 16:17:25 2014 +1200
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Fri Jun 6 14:21:42 2014 +1200

    revalidator: Replace ukey-&gt;mark with dump_seq.
    
    Rather than setting and resetting the 'mark' field in the ukey, this
    patch introduces a seq to track whether a flow has been seen during the
    most recent dump. This tidies the code and simplifies the logic for
    detecting when flows are duplicated from the datapath.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
