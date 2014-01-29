---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8f1686dd-8999-416e-b559-45cb30348ee9
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 9228ecaf-32c4-40ae-9585-2084e10b2ed7
controller          : [75a251ae-77a9-4059-a48c-f20fb72a80c7]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [54d67caf-38f9-4d47-8e54-4b2e2561304b, 8f431cb6-25a9-455a-bcc1-ae46cf8e481e, e1114034-4562-49b8-8abb-d2f4bb29c663]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 75a251ae-77a9-4059-a48c-f20fb72a80c7
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=301, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e1114034-4562-49b8-8abb-d2f4bb29c663
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0c145e1f-2b92-4620-9c9c-6556591894e2]
name                : eth7

_uuid               : 8f431cb6-25a9-455a-bcc1-ae46cf8e481e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ffa720e6-b1fc-4f76-808d-a501dceb770b]
name                : br0

_uuid               : 54d67caf-38f9-4d47-8e54-4b2e2561304b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [44a5b8fa-e16d-4c8b-82fb-8cded97c0943]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ffa720e6-b1fc-4f76-808d-a501dceb770b
admin_state         : up
duplex              : full
ifindex             : 87
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

_uuid               : 44a5b8fa-e16d-4c8b-82fb-8cded97c0943
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=455154, tx_dropped=0, tx_errors=0, tx_packets=4862}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 0c145e1f-2b92-4620-9c9c-6556591894e2
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
statistics          : {collisions=0, rx_bytes=3052863995, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72530035, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 08d74a962e302b752f53a9c367053a39068104ed
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Tue Jan 28 13:04:35 2014 -0800
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Tue Jan 28 16:07:29 2014 -0800

    upcall: Avoid divide-by-zero calculating flow limit
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
