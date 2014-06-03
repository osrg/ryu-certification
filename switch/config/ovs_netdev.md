---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
25683556-a98d-44c8-b29c-8ad8bb395f48
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 6a1b83e8-dff7-440b-ba7e-f00615beaded
controller          : [4379012a-9738-440d-a0a1-9ba6003816fb]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [02053954-3981-4551-9b99-792aded8c733, 65873fec-a61d-4c6c-9a9a-c8358c8c92a5, 7497c9c0-db7a-4b3b-9960-ebd6b6b2a77b, bc0bd681-b2e8-4e61-a146-cc63191ae06f]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4379012a-9738-440d-a0a1-9ba6003816fb
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=962, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7497c9c0-db7a-4b3b-9960-ebd6b6b2a77b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fb7ebe3e-d5ec-42a8-acb7-b41bac17e2ec]
name                : eth22

_uuid               : 02053954-3981-4551-9b99-792aded8c733
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1402add3-abbe-4407-8b37-5c9b7d19460a]
name                : eth23

_uuid               : 65873fec-a61d-4c6c-9a9a-c8358c8c92a5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1ff488cf-833b-457c-b601-44c5f3a1112d]
name                : br0

_uuid               : bc0bd681-b2e8-4e61-a146-cc63191ae06f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4f89f383-8cdd-4479-b64a-59906ff0f3c5]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : fb7ebe3e-d5ec-42a8-acb7-b41bac17e2ec
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2557524774, tx_dropped=0, tx_errors=0, tx_packets=4584518}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 1ff488cf-833b-457c-b601-44c5f3a1112d
admin_state         : down
duplex              : full
ifindex             : 336
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

_uuid               : 4f89f383-8cdd-4479-b64a-59906ff0f3c5
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
statistics          : {collisions=0, rx_bytes=2931559888, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=10589859, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 1402add3-abbe-4407-8b37-5c9b7d19460a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3400194704, tx_dropped=0, tx_errors=0, tx_packets=5130108}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 07383e165e7e7ec2d94ea9066568dcda1a400d08
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Tue Jun 3 12:21:38 2014 +1200
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Tue Jun 3 12:28:03 2014 +1200

    revalidator: Fix a build issue.
    
    Commit acaa8dac490cc6c36026d45f3010ec75f38ee142 &#40;revalidator: Eliminate
    duplicate flow handling.&#41; introduced a build error. This fixes the bug.
    
    Reported-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
