---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9e33b075-756b-4291-915a-ad7c17a1fdc4
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b1dad869-ede9-4d45-a9e7-a97d71bd5e3d
controller          : [3e2feffd-9cab-4c91-bbbb-6aa02519bdf3]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [38f178e2-017d-4ed3-a3ae-49d76790eec8, 8673534f-798d-452a-8908-9cf50aeff27f, 9c8ca3e4-a1b7-4805-9442-b5409cf455ca, d6a790a6-036f-436a-a802-e75a816a2525]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3e2feffd-9cab-4c91-bbbb-6aa02519bdf3
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=817, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9c8ca3e4-a1b7-4805-9442-b5409cf455ca
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fbae4598-b04d-4ab1-896c-7bf59697ad35]
name                : eth23

_uuid               : 38f178e2-017d-4ed3-a3ae-49d76790eec8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f1ab740b-e3d4-4f12-b789-5377317a8127]
name                : br0

_uuid               : d6a790a6-036f-436a-a802-e75a816a2525
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a31c43cf-3086-4192-a27e-5de3c0c57100]
name                : eth21

_uuid               : 8673534f-798d-452a-8908-9cf50aeff27f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6f3a7ce3-3740-4a76-98fa-9502a4268115]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : fbae4598-b04d-4ab1-896c-7bf59697ad35
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2044732408, tx_dropped=0, tx_errors=0, tx_packets=7089778}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f1ab740b-e3d4-4f12-b789-5377317a8127
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

_uuid               : a31c43cf-3086-4192-a27e-5de3c0c57100
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
statistics          : {collisions=0, rx_bytes=1894404157, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=161691273, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6f3a7ce3-3740-4a76-98fa-9502a4268115
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2386770934, tx_dropped=0, tx_errors=0, tx_packets=98980979}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d752e05420405fe97b9861484efc767d4bb114c7
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Sun Oct 12 20:56:19 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Oct 13 14:01:40 2014 -0700

    datapath-windows: loop iterator fixes in Vport.c
    
    Validation:
    - With these fixes, we no longer see the freeze during module
    uninstallation or when we try to add a new port.
    - We are able to add a port called &quot;internal of type internal using:
    ovs-dpctl.exe add-if ovs-system internal,type=internal
    
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Tested-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
