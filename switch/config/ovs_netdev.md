---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
cc18cd2f-96a4-43a3-af36-04bd1c0db4c7
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e5503cf3-b6df-4c4a-aafe-39fe9aff3988
controller          : [eba15c28-81d8-4ee1-9170-696dce6932d7]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2417863d-f4c6-41dc-97a5-8a08a2cb6f74, 4e4271ff-33ee-49ec-8037-23eb1c7fc77a, 5ff5dc97-aa13-4cbf-8892-a4675e9731af, b8c616a2-1c49-4ae5-9f5f-a0f8b3cc201b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : eba15c28-81d8-4ee1-9170-696dce6932d7
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=977, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2417863d-f4c6-41dc-97a5-8a08a2cb6f74
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9aa59046-1312-4298-ae94-561cae877d90]
name                : eth22

_uuid               : b8c616a2-1c49-4ae5-9f5f-a0f8b3cc201b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [af68ab58-aa08-43bd-be08-0e00e3a4d823]
name                : eth21

_uuid               : 4e4271ff-33ee-49ec-8037-23eb1c7fc77a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5644ce9d-201a-414c-a23f-9c59781484ee]
name                : br0

_uuid               : 5ff5dc97-aa13-4cbf-8892-a4675e9731af
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [67364375-972e-44c2-8bd7-3032f5712e83]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : af68ab58-aa08-43bd-be08-0e00e3a4d823
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
statistics          : {collisions=0, rx_bytes=1125562078, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=81034644, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 5644ce9d-201a-414c-a23f-9c59781484ee
admin_state         : down
duplex              : full
ifindex             : 597
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

_uuid               : 67364375-972e-44c2-8bd7-3032f5712e83
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2447387080, tx_dropped=0, tx_errors=0, tx_packets=10222210}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9aa59046-1312-4298-ae94-561cae877d90
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3206529764, tx_dropped=0, tx_errors=0, tx_packets=33677341}
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
