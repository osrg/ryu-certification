---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c290add8-2274-43ae-bcb5-3a08c4602557
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 73e309fb-25eb-4935-9c90-61f484cd0e6a
controller          : [88d8058c-2856-4a82-ad6a-62a1d52c2e3a]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [589ec974-3810-449e-8e59-5da9d360783b, 61093b85-3aa5-404d-804a-5ca2d336f4f7, 8efb1e3d-2eac-45cf-8649-881d0ab424e8, d5197e51-976a-4a78-b4a4-1c26f2703553]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 88d8058c-2856-4a82-ad6a-62a1d52c2e3a
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="652", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 589ec974-3810-449e-8e59-5da9d360783b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3da52521-4a42-4f59-b200-f01b24559638]
name                : "eth23"

_uuid               : 8efb1e3d-2eac-45cf-8649-881d0ab424e8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8018dedd-d202-4796-a043-e72a5b13dff8]
name                : "br0"

_uuid               : 61093b85-3aa5-404d-804a-5ca2d336f4f7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1758e83e-70ab-425c-b604-16c0df7d1d4e]
name                : "eth21"

_uuid               : d5197e51-976a-4a78-b4a4-1c26f2703553
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [efda8bb2-feb5-4f9f-8c23-3259ad22bb40]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3da52521-4a42-4f59-b200-f01b24559638
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=41546299500, tx_dropped=0, tx_errors=0, tx_packets=27697533}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 8018dedd-d202-4796-a043-e72a5b13dff8
admin_state         : down
duplex              : full
ifindex             : 909
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : 1758e83e-70ab-425c-b604-16c0df7d1d4e
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=1232426933611, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=821994762, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : efda8bb2-feb5-4f9f-8c23-3259ad22bb40
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=630521743737, tx_dropped=0, tx_errors=0, tx_packets=420513803}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f097013adabf50cf8d82562f0893d60999294bba
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Wed Apr 15 17:10:50 2015 +0900
Commit:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
CommitDate: Thu Apr 16 15:08:48 2015 +0900

    run-ryu: Use the IANA OpenFlow port number
    
    Specify the use of the port 6653 for ryu side explicitly
    because it still defaults to port 6633.
    
    Fixes check-ryu after commit d4763d1d4efbbcfd884df2d668980d61ec89d75a.
    &#40;&quot;Use the IANA-assigned ports for OpenFlow and OVSDB.&quot;&#41;
    
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
