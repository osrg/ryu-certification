---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0bc6a508-6e7f-4dd1-89a8-e97a4fa8c0cf
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
_uuid               : f5471107-f990-46d9-ae99-3e985fbd7c85
controller          : [6498c949-f57b-4a8c-b7d7-a11765ff71ce]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [67e971ef-3c42-48f4-a76f-7956452909e0, 79689d7b-39d4-4d6e-a4a9-11e80f1381f3, c89a7aa2-dead-4b44-9882-18f68636b15c, e5798e01-14cc-4baa-a64c-2f780fdb9875]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6498c949-f57b-4a8c-b7d7-a11765ff71ce
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=962, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e5798e01-14cc-4baa-a64c-2f780fdb9875
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8f3c3589-df86-4882-a479-834a30624217]
name                : br0

_uuid               : c89a7aa2-dead-4b44-9882-18f68636b15c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [30a03cbf-43d3-42fb-8305-a8c5c06d4d15]
name                : eth22

_uuid               : 67e971ef-3c42-48f4-a76f-7956452909e0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cee930f5-dc50-4ad7-8279-030e53deeb2f]
name                : eth21

_uuid               : 79689d7b-39d4-4d6e-a4a9-11e80f1381f3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1c8d41d6-fe54-4619-92e9-d99e6f4fabad]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : cee930f5-dc50-4ad7-8279-030e53deeb2f
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
statistics          : {collisions=0, rx_bytes=78034182, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=25884986, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8f3c3589-df86-4882-a479-834a30624217
admin_state         : down
duplex              : full
ifindex             : 414
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

_uuid               : 1c8d41d6-fe54-4619-92e9-d99e6f4fabad
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1217875408, tx_dropped=0, tx_errors=0, tx_packets=6538540}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 30a03cbf-43d3-42fb-8305-a8c5c06d4d15
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1123478560, tx_dropped=0, tx_errors=0, tx_packets=12225147}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 14073368d03bf4b0f4f1ecd3858dfc715d6d8d79
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Tue May 27 11:54:07 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Tue Jun 10 07:47:45 2014 -0700

    testsuite.at: pids can have zero after first character.
    
    Fix the bug which did not kill the processes with pids that had
    a zero in them. Also, some tests do a AT_CHECK&#40;[kill ]&#41; which
    on windows prints something on the stdout causing the tests to fail.
    So supress it.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
