---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
387b0d97-e183-4d04-8731-a56396ca931e
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f2641403-4e4c-49a1-b4a7-27db55b17a4f
controller          : [ac2d0810-3307-447f-b760-76155e303df6]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [13421b0b-b15a-4268-8dd9-f14080199d64, 4250c99e-9a9e-46ee-b8b7-d916d62e2f88, 891ae84f-e220-48bd-9727-940ac4184284, a6de9484-4772-487b-9d9b-236cf39f7f89]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ac2d0810-3307-447f-b760-76155e303df6
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=981, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a6de9484-4772-487b-9d9b-236cf39f7f89
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a01b00c2-6a48-4d34-a32d-7f04698c5b14]
name                : br0

_uuid               : 4250c99e-9a9e-46ee-b8b7-d916d62e2f88
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6e25f91c-caf5-4cbe-96ae-7e0bdd445ff7]
name                : eth22

_uuid               : 891ae84f-e220-48bd-9727-940ac4184284
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [83581b93-d031-4cc0-8857-f651443e7cf6]
name                : eth23

_uuid               : 13421b0b-b15a-4268-8dd9-f14080199d64
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bd3f5ec6-71b5-4485-b8a5-08c6fb5b3a2c]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6e25f91c-caf5-4cbe-96ae-7e0bdd445ff7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3247393098, tx_dropped=0, tx_errors=0, tx_packets=33704815}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a01b00c2-6a48-4d34-a32d-7f04698c5b14
admin_state         : down
duplex              : full
ifindex             : 599
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

_uuid               : bd3f5ec6-71b5-4485-b8a5-08c6fb5b3a2c
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
statistics          : {collisions=0, rx_bytes=1242460574, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=81113207, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 83581b93-d031-4cc0-8857-f651443e7cf6
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2546787580, tx_dropped=0, tx_errors=0, tx_packets=10288477}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a4fcb111ceb885becb6d02683d72658ea4e1a039
Author:     Lorand Jakab &lt;lojakab@cisco.com&gt;
AuthorDate: Mon Jun 23 13:48:38 2014 +0300
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Mon Jun 23 11:54:01 2014 -0700

    datapath/linux: add vport-geneve.c to .gitignore
    
    Signed-off-by: Lorand Jakab &lt;lojakab@cisco.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
