---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b1b333a5-aebe-4fcc-b6c4-fb102537e51b
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : acbb1ab7-337f-4dca-a768-000625494661
controller          : [6ba62ce4-f29c-4ba1-bf94-e469b1cc7ab5]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [96dc5156-e7bf-4290-8d82-09041a9b5431, 9c78ed54-e3be-4c50-b5fc-84db6ccc219c, bd46ee83-a9c4-4d60-a284-7204739574e8, db3900d5-f7e4-4d52-99fe-02f54d9274eb]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6ba62ce4-f29c-4ba1-bf94-e469b1cc7ab5
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9c78ed54-e3be-4c50-b5fc-84db6ccc219c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [63079f41-81fd-4a5e-aafe-0c4c02b98b0d]
name                : "br0"

_uuid               : db3900d5-f7e4-4d52-99fe-02f54d9274eb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [56bb7fd0-e381-4fc2-aa9d-42b9e2a857b9]
name                : "eth23"

_uuid               : 96dc5156-e7bf-4290-8d82-09041a9b5431
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e4c2ada3-9b64-4833-a860-ee48aeded862]
name                : "eth21"

_uuid               : bd46ee83-a9c4-4d60-a284-7204739574e8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [965d08d9-8b92-44af-9e8c-428a1bf293fb]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 56bb7fd0-e381-4fc2-aa9d-42b9e2a857b9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6556353000, tx_dropped=0, tx_errors=0, tx_packets=4370902}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 965d08d9-8b92-44af-9e8c-428a1bf293fb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29330134479, tx_dropped=0, tx_errors=0, tx_packets=19575969}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 63079f41-81fd-4a5e-aafe-0c4c02b98b0d
admin_state         : down
duplex              : full
ifindex             : 686
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

_uuid               : e4c2ada3-9b64-4833-a860-ee48aeded862
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
statistics          : {collisions=0, rx_bytes=42512963501, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28392363, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 4e548ad9e60f8248090a467fefcc58da5f298c96
Author:     Mengke Liu &lt;mengke.liu@intel.com&gt;
AuthorDate: Wed Dec 16 02:47:50 2015 +0800
Commit:     Jesse Gross &lt;jesse@kernel.org&gt;
CommitDate: Tue Dec 15 13:06:11 2015 -0800

    geneve-map-rename: rename geneve-map to tlv-map.
    
    This patch renames the command name related with geneve-map to a more
    generic name as following:
    add-geneve-map -&gt; add-tlv-map
    del-geneve-map -&gt; del-tlv-map
    dump-geneve-map -&gt; dump-tlv-map
    
    It also renames the Geneve_table to tlv_table.
    
    By doing this renaming, the NSH variable context header &#40;the same TLV
    format as Geneve&#41; or other protocol can reuse the field tun_metadata&lt;N&gt;
    in the future.
    
    Signed-off-by: Mengke Liu &lt;mengke.liu@intel.com&gt;
    Signed-off-by: Ricky Li &lt;ricky.li@intel.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@kernel.org&gt;
</pre>
