---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f3b178c7-c547-4a5c-a7ee-17f307129c38
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 4f6739cc-7437-4990-9801-cb91456501b5
controller          : [09e8b696-e95f-4aae-894c-f7b09ec4fd2f]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [326b10eb-0adb-45ec-ac57-4172f9403e1c, 54e3c336-bd91-4cd8-af6f-b5f1012ff499, 5e531a7e-c15e-44b9-acfc-cf99fc1b0f19, 771b0c6c-a1d5-45de-8b68-1cc0313a434c]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 09e8b696-e95f-4aae-894c-f7b09ec4fd2f
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="647", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 771b0c6c-a1d5-45de-8b68-1cc0313a434c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e1454feb-d262-4648-bcf4-578f16755d86]
name                : "eth21"

_uuid               : 54e3c336-bd91-4cd8-af6f-b5f1012ff499
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1a8ecbc0-251f-4ecf-87db-df637799c078]
name                : "eth22"

_uuid               : 5e531a7e-c15e-44b9-acfc-cf99fc1b0f19
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [48c86769-ddd4-48d2-ad65-1f2d37cc9265]
name                : "br0"

_uuid               : 326b10eb-0adb-45ec-ac57-4172f9403e1c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [42f23403-7481-4b16-82f9-54a651f6261f]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1a8ecbc0-251f-4ecf-87db-df637799c078
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9991065586, tx_dropped=0, tx_errors=0, tx_packets=6664204}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 48c86769-ddd4-48d2-ad65-1f2d37cc9265
admin_state         : down
duplex              : full
ifindex             : 47
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

_uuid               : 42f23403-7481-4b16-82f9-54a651f6261f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=923631000, tx_dropped=0, tx_errors=0, tx_packets=615754}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : e1454feb-d262-4648-bcf4-578f16755d86
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
statistics          : {collisions=0, rx_bytes=12513561896, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=8350202, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
