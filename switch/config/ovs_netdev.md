---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
06e7997f-aa2f-4966-be3e-d1e59ccba8b0
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 2bf43f3b-7ace-43a7-97c3-aca2d16641d9
controller          : [9d897e58-26f1-4b55-b05a-bb24e38186bb]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [17e9d395-9d4a-4bb7-95f2-d22017ca8019, 68d0c3b0-5fd8-4acf-a638-80e16a64947e, 8f645a61-39dd-49d7-82d2-ad3b2fbd2034, cf77bc8e-6aad-49cb-8d8b-7535e521d284]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9d897e58-26f1-4b55-b05a-bb24e38186bb
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=567, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 68d0c3b0-5fd8-4acf-a638-80e16a64947e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7667ceb1-f84c-4282-81af-e5bd224deecb]
name                : eth21

_uuid               : 8f645a61-39dd-49d7-82d2-ad3b2fbd2034
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [999052b8-bc6f-487c-adfe-0edc62a4cc12]
name                : eth23

_uuid               : 17e9d395-9d4a-4bb7-95f2-d22017ca8019
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8ed9a10e-e03c-495f-a93a-15c92ed7c0c9]
name                : eth22

_uuid               : cf77bc8e-6aad-49cb-8d8b-7535e521d284
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8274f90c-7018-4902-a76c-75547c43af20]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8274f90c-7018-4902-a76c-75547c43af20
admin_state         : down
duplex              : full
ifindex             : 1159
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

_uuid               : 999052b8-bc6f-487c-adfe-0edc62a4cc12
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1500
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2051491500, tx_dropped=0, tx_errors=0, tx_packets=1367661}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 7667ceb1-f84c-4282-81af-e5bd224deecb
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=3685406098, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2475447, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8ed9a10e-e03c-495f-a93a-15c92ed7c0c9
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1500
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2046914988, tx_dropped=0, tx_errors=0, tx_packets=1372016}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a7ae938074d1c5e25e484eb7b6aca3f101adea38
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Apr 24 15:35:35 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Apr 24 15:37:24 2014 -0700

    FAQ: Explain what to do when building against a too-new kernel.
    
    Also add references to this FAQ from INSTALL and configure.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
