---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
5bba8a25-2f22-4a7c-8eca-8a46d7c02d01
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 1ae82304-32d7-47ed-a8fa-2d6345972ba2
controller          : [306be41b-9d7b-4409-bcb7-66b7e0c56a9f]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [02f4c5a3-1861-49e2-bb85-1760ab0bc8c8, 26f585eb-90e8-4aec-8ca9-22252b0d656f, b84f9c86-83d9-40f6-a195-10aa1de5ef51, ff2922d8-586d-4b0e-b5a5-bfaaf1bef12e]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 306be41b-9d7b-4409-bcb7-66b7e0c56a9f
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ff2922d8-586d-4b0e-b5a5-bfaaf1bef12e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [56d57cb5-d5b5-437d-afc4-eb91a3a08596]
name                : "eth21"

_uuid               : b84f9c86-83d9-40f6-a195-10aa1de5ef51
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f4746afd-50de-4b58-97ae-e7a9e492c467]
name                : "eth23"

_uuid               : 02f4c5a3-1861-49e2-bb85-1760ab0bc8c8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [04201bcd-7082-4712-869d-ae00b0060ea9]
name                : "br0"

_uuid               : 26f585eb-90e8-4aec-8ca9-22252b0d656f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c57b5fe0-6a8a-486f-b296-601286cbe4a2]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c57b5fe0-6a8a-486f-b296-601286cbe4a2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31700128440, tx_dropped=0, tx_errors=0, tx_packets=21170390}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f4746afd-50de-4b58-97ae-e7a9e492c467
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10503243000, tx_dropped=0, tx_errors=0, tx_packets=7002162}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 04201bcd-7082-4712-869d-ae00b0060ea9
admin_state         : down
duplex              : full
ifindex             : 860
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

_uuid               : 56d57cb5-d5b5-437d-afc4-eb91a3a08596
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
statistics          : {collisions=0, rx_bytes=47778728822, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31932463, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6019cb63956dc87afd130c31ac17137d1304a931
Author:     Ilya Maximets &lt;i.maximets@samsung.com&gt;
AuthorDate: Thu Mar 3 11:30:06 2016 +0300
Commit:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
CommitDate: Sat Mar 5 20:15:25 2016 -0800

    netdev-dpdk: Fix memory leak in netdev_dpdk_vhost_destruct&#40;&#41;.
    
    Fixes: 4573fbd38fa1 &#40;&quot;netdev-dpdk: Add vhost-user multiqueue support&quot;&#41;
    Signed-off-by: Ilya Maximets &lt;i.maximets@samsung.com&gt;
    Acked-by: Flavio Leitner &lt;fbl@sysclose.org&gt;
    Acked-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>
