---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f6f584ab-a062-4940-a575-7345f7760739
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 03032711-a474-4f22-80f5-13bf2fe549d2
controller          : [4aa9ea8c-bcbb-4dca-93fe-4378bc6d982c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [162bfe38-45c9-41a2-aece-289414a7e007, 5334396d-c9a4-4d32-b145-d59562d701f0, 9aff22ed-50db-4c19-9568-93d0d772a976, dc697eed-8106-4e52-8baa-bacc425ce0f2]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4aa9ea8c-bcbb-4dca-93fe-4378bc6d982c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 162bfe38-45c9-41a2-aece-289414a7e007
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f42fe218-46f4-4b7c-bc89-98d4b7861446]
name                : "eth21"

_uuid               : dc697eed-8106-4e52-8baa-bacc425ce0f2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [36f07d6c-ee78-44fc-a42c-47160924d9d8]
name                : "eth23"

_uuid               : 5334396d-c9a4-4d32-b145-d59562d701f0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fc272e97-b0a5-4b33-be6c-db34486f0cc5]
name                : "eth22"

_uuid               : 9aff22ed-50db-4c19-9568-93d0d772a976
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0a4db5ad-4ace-4c10-8bfd-65c93c05278d]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 36f07d6c-ee78-44fc-a42c-47160924d9d8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7170787500, tx_dropped=0, tx_errors=0, tx_packets=4780525}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f42fe218-46f4-4b7c-bc89-98d4b7861446
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
statistics          : {collisions=0, rx_bytes=43332106722, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28943057, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 0a4db5ad-4ace-4c10-8bfd-65c93c05278d
admin_state         : down
duplex              : full
ifindex             : 710
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

_uuid               : fc272e97-b0a5-4b33-be6c-db34486f0cc5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29698355144, tx_dropped=0, tx_errors=0, tx_packets=19823689}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9415556b51e75b4f9804a669884e26850c31e846
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Mon Dec 7 15:13:03 2015 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Wed Dec 23 09:20:40 2015 -0800

    datapath-windows: Reduce padding size in _OVS_PACKET_HDR_INFO.
    
    Fixes: efee3309 &#40;&quot;datapath-windows: Support for OVS_KEY_ATTR_SCTP attribute&quot;&#41;
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
    Acked-by: Sairam Venugopal &lt;vsairam@vmware.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
</pre>
