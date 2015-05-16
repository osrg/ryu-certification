---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
30f52381-febf-47f2-9fca-081a673a4e97
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d92b5a07-df72-40c4-a9a9-c0763b757d37
controller          : [a9609954-2dea-475d-a37d-bafcd3ae5356]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2259aa0d-b0b8-4ff9-a29a-3200040840c6, 99bf0822-ad2e-447c-9d6b-f8988877974b, bcc1cccb-f0ec-484b-b1fc-d4faabefb19a, c049137a-b06e-4e52-ba95-f998568f9369]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a9609954-2dea-475d-a37d-bafcd3ae5356
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="661", sec_since_disconnect="4", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2259aa0d-b0b8-4ff9-a29a-3200040840c6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [50d0c884-952c-47bc-b240-481acb77e5fc]
name                : "eth22"

_uuid               : 99bf0822-ad2e-447c-9d6b-f8988877974b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dd55227d-4fd0-478f-acb9-f4600cf86986]
name                : "br0"

_uuid               : c049137a-b06e-4e52-ba95-f998568f9369
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3a93d946-43b6-4855-b8a3-44aa7933e2df]
name                : "eth21"

_uuid               : bcc1cccb-f0ec-484b-b1fc-d4faabefb19a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dcf27118-733c-4cf0-8afd-6b8193447b48]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : dcf27118-733c-4cf0-8afd-6b8193447b48
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=836122500, tx_dropped=0, tx_errors=0, tx_packets=557415}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 50d0c884-952c-47bc-b240-481acb77e5fc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9938231309, tx_dropped=0, tx_errors=0, tx_packets=6628677}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : dd55227d-4fd0-478f-acb9-f4600cf86986
admin_state         : down
duplex              : full
ifindex             : 45
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

_uuid               : 3a93d946-43b6-4855-b8a3-44aa7933e2df
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
statistics          : {collisions=0, rx_bytes=12396585071, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=8271575, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 91f831671269ade5e936812ae1dc1950105c748d
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Fri May 15 06:32:32 2015 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Fri May 15 21:10:26 2015 -0700

    datapath: Fix Sparse warning.
    
    CHECK   /home/pravin/ovs/w8/datapath/linux/flow_table.c
    /home/pravin/ovs/w8/datapath/linux/flow_table.c:536:6: warning: symbol
    'ovs_flow_cmp_unmasked_key' was not declared. Should it be static?
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
